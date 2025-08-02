
# PROGRAMMING WITH UNIX

By: Sumeet Singh @ sumeet-singh.com

Date: July 2024

# TABLE OF CONTENTS
- [1. Terminologies](#terminologies)
- [2. Requirements](#requirements)
- [3. Installing](#installing)
- [4. First time setup](#first-time-setup)
- [5. Profile script](#profile-script)
- [6. Common Commands](#common-commands)
- [7. Scripts](#scripts)

# TERMINOLOGIES

# REQUIREMENTS

The commands below target the Debian family e.g. Debian, Ubuntu, RaspberryPi
However the same principal can be applied to many other distros 


# INSTALLING

Linux is a free and open-source operating system, originally based on the Unix OS. It was created by Linus Torvalds in 1991 when he released the first version of the Linux kernel. Since then, Linux has grown into a highly versatile and widely used system, with a variety of distributions (distros) available for different purposes. The term distro refers to a specific version of Linux, customized with additional software and configuration, often targeting specific user needs.

Anyone can take the Linux kernel and create their own custom distro. These distros can be free, open-source, or paid. Open-source distros are typically maintained by communities and are often available on platforms like GitHub, where anyone can contribute. However, these community-driven distros may not have the resources or manpower that enterprise companies have, so they might not always have the latest hardware drivers or support for new technologies.

Each Linux distro includes its own set of command-line tools and online software repositories, maintained by the community. These repositories offer software packages that can be installed either via the command line or through graphical user interfaces (GUIs). For example, package management systems like apt (Debian-based distros like Ubuntu) and yum (Red Hat-based distros like CentOS) are used to install and manage software. Both have the same purpose but differ in commands, syntax, and package formats. Apt uses .deb packages, while Yum uses .rpm. Additionally, distros like Arch Linux offer a rolling release system, which means they provide continuous updates rather than major version upgrades.

Linux Kernel:
At the core of any Linux-based operating system is the Linux kernel, which is the heart of the system that interacts with the hardware. The kernel is responsible for managing resources, memory, processes, hardware devices, and security. Without the kernel, the rest of the operating system wouldn't be able to function.

Daemons:
In Linux, a daemon is a background process that runs without direct interaction from the user. These processes manage system services like networking, printing, or system logging. Common daemons include the web server (Apache), database management systems (MySQL), or network-related processes (sshd). Daemons typically start when the system boots up and continue running until the system is shut down.

Distros for Different Purposes:

Kali Linux is designed for penetration testing and hacking, offering a wide array of security and forensic tools. It’s ideal for ethical hackers and security professionals looking for a ready-made, robust platform for testing vulnerabilities.
Ubuntu is one of the most popular Linux distros for general-purpose use. It's known for being user-friendly, making it great for beginners. It’s ideal for home use, web browsing, gaming, and entertainment. Ubuntu has a large software repository and active community support, making it easy for users to find solutions to problems.
Linux Mint is another distro that's aimed at providing a familiar user interface for those coming from Windows, making it great for people who want a smooth desktop experience with multimedia capabilities.
Arch Linux is a more advanced distro that provides minimalism and customization, allowing users to build their system from the ground up. It's a good option for power users who prefer control over their system.
Red Hat Enterprise Linux (RHEL) and CentOS (a free RHEL clone) are often used in enterprise environments for their stability and long-term support.
Why Linux is Used in Business & Home Environments: Like Windows, Linux is widely used in both home and commercial environments. In the business world, distros like CentOS, Ubuntu Server, and Red Hat are deployed as servers, providing essential services such as web hosting, domain control, email servers, and network management. On the home front, distros like Ubuntu or Linux Mint are commonly used for everyday computing tasks like web browsing, entertainment, gaming, and office productivity.

1. INSTALLING UBUNTU
```bash
1. Download the **Ubuntu** ISO from the official website:
   - [Ubuntu Download](https://ubuntu.com/download/desktop) (For the regular desktop version)
   - [Ubuntu Server Download](https://ubuntu.com/download/server) (For the server version)
   - **Ubuntu**: This is the regular desktop version, which includes a **Graphical User Interface (GUI)** by default, designed for home or office use. It’s easy to use, with all the tools you need for general-purpose computing like web browsing, gaming, office apps, etc.
   - **Ubuntu Server**: This version is designed for **server environments**, meaning it doesn’t come with a GUI by default. It’s meant for users who want to set up web servers, database servers, file servers, etc., and prefer to use the command line for managing the system. However, you can install a GUI later if you prefer.

2. Connect a USB drive to the destination computer where you want to install Ubuntu.

3. Download and install **Rufus** from:
   - [Rufus Download](https://rufus.ie/)

4. Open **Rufus**:
   - Select the **USB drive** from the "Device" dropdown.
   - Under "Boot selection," click **Select** and choose the **Ubuntu ISO** you downloaded in step 1.
   - Ensure that the **Partition Scheme** is set to **GPT** and the **File System** is **FAT32** (default for most cases).
   - Click **Start** to begin creating the bootable USB.

5. Once the process is complete, safely eject the USB and insert it into the computer where you want to install Ubuntu.

6. Boot the computer into BIOS (usually by pressing a key like **F12**, **ESC**, or **DEL** during startup).
   - In BIOS, select the boot options and choose to boot from the **EFI USB Device**.
   - Save the changes and exit BIOS.

7. Once Ubuntu starts loading, follow the on-screen prompts to complete the installation.
   - You'll be prompted to set up a **user account**. Enter your **username** and **password** for the system.
   - You will also be asked if you want to set up a **Graphical User Interface (GUI)** or proceed with a **command-line only** setup:
     - **For Ubuntu Desktop**: The GUI is pre-installed, so you’ll get a full desktop environment like you would on a regular personal computer.
     - **For Ubuntu Server**: You will install the system without a GUI, using the command line interface (CLI). If you later decide you want a GUI, you can install one (such as **GNOME**, **KDE**, or **XFCE**) using the terminal.

8. If prompted, set up your Wi-Fi by selecting your network and entering the necessary credentials.
```


# FIRST TIME SETUP

The following commands all the Debian (Which includes Ubuntu) distrobution commands.
However the same principal can be applied to many other distros 

1. (OPTIONAL FOR VIRTUAL BOX USERS) - CREATE ADMINS
```bash
su
usermod -aG sudo vboxuser # or wheel group
cat /etc/sudoers
exit
sudo reboot # necessary to reset admin cache
```

2. UPDATE
```bash
sudo apt update
sudo apt upgrade -y
sudo apt dist-upgrade -y
sudo reboot
# or
pacman -Syu
```

3. CHECK DRIVERS ALL INSTALLED
```bash
dmesg # check kernel for hardware/driver errors then fix/install
```

4. ENABLE SSH
```bash
sudo apt install openssh-server -y # for incomming SSH
```

5. HARDEN
```bash
sudo apt install ufw
sudo ufw enable
sudo ufw allow ssh
sudo ufw status
```

6. OPTIONAL - SETUP GUI
```bash
sudo apt install ubuntu-desktop # ubuntu, or for low OS spec hardware install lubuntu-desktop
```

7. OPTIONAL - ENABLE INLINE COMMENTS
```bash
testusr@ubuntu Documents % setopt interactive_comments # zsh shell only
```

8. OPTIONAL - USEFULL PACKAGES
```bash
sudo apt install lolcat, git, flatpak
```

9. OPTIONAL - SETUP C/C++ COMPILER
```bash
# 1. INSTALL USEFULL PACKAGES 
sudo apt install -y build-essential g++ libboost-all-dev libcurl4-gnutls-dev 
libzip-dev libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev 
zlib1g-dev googletest libgtest-dev yasm cmake git
# 2. Test C code
echo "#include <stdio.h>" > test.c
echo 'int main() { printf("Hello, world!\\n"); return 0; }' >> test.c
gcc -o test test.c
./test
```

10. CLEANUP
```bash
sudo snap remove firefox
```

___________________________________________________________________________

# PROFILE SCRIPT

1. Open your shells startup script
```bash
ls -la ~ # first find the default shell used by querying hidden folders in home.
sudo nano ~/.zshrc # Mac
sudo nano ~/.bashrc # Ubuntu
```

2. Add your startup code
```bash
sumeetsingh@Sumeets-Air-2 sandbox % cat ~/.zshrc   
export PATH="/opt/homebrew/opt/llvm/bin:$PATH"
export PATH="/opt/homebrew/Cellar/ruby/3.3.2/bin:$PATH" # brew install ruby

# ZSH SHELL ONLY
setopt interactive_comments # enables inline CLI comments in zsh with # e.g. % echo test # test comment

runlolcat() {
    local cmd="$1"
    shift
    command "$cmd" "$@" 2>&1 | lolcat
}

# Aliases
alias ls='runlolcat ls'
alias cat='runlolcat cat'
alias grep='runlolcat grep'
alias tail='runlolcat tail'
alias head='runlolcat head'
```

# COMMON COMMANDS

SSH INTO LINUX DEVICE
```bash
# e.g. a Raspberry Pi on home network uses default password raspberry
ssh pi@192.168.0.211
pi@retropi:~ enter password $ raspberry
```

FIND OS | DISTRIBUTION | RELEASE | VERSION
```bash
cat /etc/os-release

pi@retropie:~ $ cat /etc/os-release
PRETTY_NAME="Raspbian GNU/Linux 10 (buster)"
NAME="Raspbian GNU/Linux"
VERSION_ID="10"
VERSION="10 (buster)"
VERSION_CODENAME=buster
ID=raspbian
ID_LIKE=debian
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"
```

FIND HIDDEN FILES
```bash
ls -la
```

ENVIRONMENTAL VARIABLES
```bash
# on Linux environmental variable refers to shell startup script file
ls -la ~ # first find the default shell used by querying hidden folders in home.
sudo nano ~/.zshrc # Mac
sudo nano ~/.bashrc # Ubuntu

# then add the filepath to the executable e.g, for FFMPEG
/usr/lib/ffmpeg
```

FIND KERNEL
```bash
pi@retropie:~ $ uname -a
Linux retropie 5.4.72-v7+ #1356 SMP Thu Oct 22 13:56:54 BST 2020 armv7l GNU/Linux

# IF KERNEL IS OLD THEN RUN
sudo apt update
# or
sudo apt full-upgrade
```

UPTIME
```bash
uptime
```

CHANGE HOSTNAME
```bash
sudo nano /etc/hostname
sudo nano /etc/hosts
#    127.0.1.1   retropie # e.g. uncommont this to rename the hostname to the IP address in /hosts
sudo reboot
```

QUITTING CLI
```bash
# option 1
press "ESC" then "w" then "q"

# option 2
q
```

NAVIGATION FILTERING
```bash
#pipe through | less
apt list --installed | grep es | less # quit with q
pi@retropie: ~ $ q # at END press q
```

MOVE CLI / TERMINAL PROMPT TO TOP OF SCREEN AGAIN
```bash
clear
```

COMMENTS
```bash
# Zsh shell only - enable inline comments with setopt
testusr@ubuntu Documents % setopt interactive_comments
testusr@ubuntu Documents % echo test # test
test

cd c:\users\sumeetsingh\Documents ; # in CLI use line break ; followed by comment
```

SEARCH - USERS
```bash
cat /etc/passwd # linux
# or
dscl . list /Users # macos
```

SEARCH AND FIND - FILES
```bash
find /usr -iname "*xxx*"
ls | grep xxx
```

SEARCH - STRING
```bash
# use awk to pattern match strings in file
awk 'pattern { action }' file

# EXAMPLE
sumeetsingh@Sumeets-Air-2 sandbox % cat CREDITS.txt                  
2D asset images from: https://2minutetabletop.com/product-category/free/
Hourglass icon by icon-icons.com @ icon-icons.com/icon/sand-clock-hourglass/191332%                                          
sumeetsingh@Sumeets-Air-2 sandbox % awk '/asset/ { print }' CREDITS.txt # <-- LOOK HERE

2D asset images from: https://2minutetabletop.com/product-category/free/
```

SEARCH - PACKAGE MANAGER
```bash
pacman -Ss xxxxx # to search with name e.g. all python packages
pacman -Q # or list all
sudo apt search xxxx
sudo apt list --installed xxxxx
```

SEARCH - SERVICES
```bash
# 3 methods are below
# 1 - through apt
apt list --installed
# 2 - through system services
systemctl list-unit-files
# 3 through manual clone/make/install etc., the binary will be put in /bin and usually in environmental variable
ls /usr/bin 
emulationstation
pi@retropi:~ $ emulationstation # to then start it
```

PROCESS
```bash
top
htop # better version
```

SERVICES
```bash
sudo systemctl status ssh # check ssh service status
sudo systemctl start ssh # restart service if off
sudo systemctl enable ssh # enable service at boot
```

RESTART SERVICE | REBOOT SERVICE | KILL SERVICE
```bash
1. # Find the services e.g, note the full name is cut off 
   PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    929 pi        20   0  580.4m 103.3m  60.0m S   5.6   1.3   0:58.05 emulationstatio
2. pkill emulationstatio # or kill by PID: sudo kill 929
3. emulationstation # restart service
```

SYMBOLIC LINKS | SYM LINKS

Symlinks: A symlink is a special type of file that points to another file or directory. When you access the symlink, the system redirects you to the target file or directory. They are useful for creating shortcuts or references to files and directories in different locations without duplicating data. Environment Variables:

Environment variables: are key-value pairs used by the operating system to configure the environment for processes. They store configuration settings, such as paths, user preferences, and system information. They can be accessed by programs and scripts to behave differently based on the environment.

Finding Symlinks:
```bash
ls -l /path/to/directory
# OR
find /path/to/directory -type l # find all symlinks in a directory

#then to find where a symlink points too
readlink /path/to/symlink
```

FIND BIN ENVIRONMENTAL VARIABLE
```bash
sumeetsingh@Sumeets-Air-2 which ruby
# or 
sumeetsingh@Sumeets-Air-2 where ruby
/usr/bin/ruby
```

FORMAT
```bash
ls | sort -h
```

LOGONS
```bash
w

# EXPLANATION
# The same user pi is logged in twice, once through hardware, once through SSH
# TTY = hardware sessions, therefore TTY1 means user is logged in through hardware on first port
# pts = Virtual terminal sessions such as through SSH, therefore pts/0 = a user is logged in through first remote session i.e SSH
pi@retropie:~ $ w
 17:59:46 up 35 min,  2 users,  load average: 0.42, 0.44, 0.38
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
pi       tty1     -                17:24   35:11  10:29  10:28  /opt/retropie/supplementary/emulationstation/emulations
pi       pts/0    192.168.0.115    17:47    2.00s  0.30s  0.01s w
```

PERMISSIONS - USER GROUPS
```bash
id pi

# EXAMPLATION
# user "pi" is the first non root user = id 1000. They are also part of sudo group 27. etc.,
# So permissions below are for a standard user 'pi' for a raspberrypi AIO computer.
pi@retropie:~ $ id pi
uid=1000(pi) gid=1000(pi) groups=1000(pi),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),44(video),46(plugdev),60(games),100(users),105(input),109(netdev),999(spi),998(i2c),997(gpio)


# NOTE: You can check your own group by just typing
groups
```

PERMISSIONS - FILE ACCESS
```bash
# e.g, making a simple script and granting file access to run
echo '#!/bin/zsh' > test.sh && echo 'figlet HELLO WORLD | lolcat' >> test.sh
# NOTE: chmod stands for Change Mode
chmod a+rwx test.sh # a = anyone, rwx = can read write execute

# you can use a (anyone), g (group), u (user), or o (others)

# you can also target the current user without specifying a specific user
chmod +rwx
# or
chmod +x # just to give execute permissions e.g. for a cron job to yourself when logged in

# REMOVE PERMISSIONS
# do the opposite with a substraction (minus) character
chmod a-rwx

# GROUP ACCESS
# to give access based on a group e.g. you want anyone in piusers to be able to run script then
# first change the group ownership of the file to group
sudo chgrp piusers test.sh
chmod g+rwx test.sh

sumeetsingh@Sumeets-Air-2 sandbox % ./test.sh
 _   _ _____ _     _     ___   __        _____  ____  _     ____  
| | | | ____| |   | |   / _ \  \ \      / / _ \|  _ \| |   |  _ \ 
| |_| |  _| | |   | |  | | | |  \ \ /\ / / | | | |_) | |   | | | |
|  _  | |___| |___| |__| |_| |   \ V  V /| |_| |  _ <| |___| |_| |
|_| |_|_____|_____|_____\___/     \_/\_/  \___/|_| \_\_____|____/ 
```

SHUTDOWNS
```bash
sudo shutdown now
# or
sudo reboot now
```

FIND PHYSICAL DISPLAY
```bash
sudo systemctl status display-manager
```

DISK FREE | DISK SPACE | DISK USAGE
```bash
 # this works on the current directory you are in
 # -h = human readable format converts the bytes to MB's
 # -d = depth, to show the subdirectories sizes within
 # -c = total = total size of this folder so ./sandbox = ~300MB's
df -h 
du -h -d 1

sumeetsingh@Sumeets-Air-2 sandbox % du -hc -d 1

188K    ./documentation
 47M    ./etc
8.0K    ./vedic
8.0K    ./headers
4.0K    ./templates
114M    ./.git
 12K    ./.vscode
130M    ./assets
  0B    ./src
292M    .
292M    total
```

COPY FILES
```bash

# rsync VS cp

# rsync only overwrites the existing destination file if they are different (sizes, types, etc.,) however with --ignore-existing it wont
# rsync can be resumed
# rsync is more network fault tolerant

# cp is faster

# CP

# use -i for confirmation before overwriting
# use -r to recurse and target contents inside folders
# use -v for verbose - best option
cp "/media/usb1/Silent Hill" /home/pi/RetroPie/roms/psx/ # COPY AND REPLACE 1 FILE
cp -rv /media/usb1/* /home/pi/RetroPie/roms/psx/ # COPY AND REPLACE ALL FOLDERS
cp -irv /media/usb1/* /home/pi/RetroPie/roms/psx/ # COPY AND ASK PERMISSION BEFORE OVERWRITING ALL FOLDERS
cp -r * ../ # COPY FOLDER CONTENTS TO PARENT
# OR use absolute path 
cp -r * /home/username/destination/  # COPY FOLDER CONTENTS TO PARENT
find . -mindepth 1 -maxdepth 1 -type d -exec cp -v -r {}/\* ../ \; # FROM PARENT DIRECTORY COPY ALL FOLDERS CONTENTS TO PARENT

# RSYNC

# use -a "archive mode" to preserve permissions, timestamps, symbolic links and other attributes of contents
# use --progress for a progress indicator
# use --ignore existing to now overwrite files that exist in destination
rsync -av --progress /media/usb1/* /home/pi/RetroPie/roms/psx/ # copy files and overwrite if different sizes
rsync -av --progress --ignore-existing /media/usb1/* /home/pi/RetroPie/roms/psx/ # copy files and dont overwrite
```

MOVE FILES
```bash
# use -i for confirmation before overwriting
mv "/media/usb1/Silent Hill" /home/pi/RetroPie/roms/psx/ # MOVE 1 FILE
mv -v /media/usb1/* /home/pi/RetroPie/roms/psx/ # MOVE ALL FOLDERS
mv -iv /media/usb1/* /home/pi/RetroPie/roms/psx/ # MOVE ALL FILES + ASK BEFORE OVERWRITING
mv * ../ # COPY FOLDER CONTENTS TO PARENT
# OR use absolute path 
mv * /home/username/destination/  # COPY FOLDER CONTENTS TO PARENT
find . -mindepth 1 -maxdepth 1 -type d -exec sh -c 'mv -v -t ../ "$1"/* && rmdir "$1"' sh {} \; && rmdir ./*
 # FROM PARENT DIRECTORY COPY ALL FOLDERS CONTENTS TO PARENT THEN DELETE EMPTY SUBDIRECTORIES
rsync -av --progress --ignore-existing /media/usb1/ /home/pi/RetroPie/roms/psx/ && rm -rf /media/usb1/* # move and delete source directories/files skipping existing
scp diablo.bin diablo.cue pi@retropie:/home/pi/RetroPie/roms/psx # secure-copy from host to dest using port 22
sftp pi@retropie ; cd /home/pi/RetroPie/roms/psx ; put file1.txt ; exit # similar to scp but more steps
```

RENAME
```bash
mv /home/me/oldName /home/me/newName  # just use move with recurse to same location
```

RESOLUTION CHANGE
```bash
# If os doesn't fit inside the window e.g. a Retropi in an arcade cabinet
# has the bottom screen e.g. the text CLI prompt part cut off, then
# adjust the padding/overlay
sudo nano /boot/config.txt
# uncomment the below and the higher the number the more it moves in so
overscan_left=5 # padding 5 from left
overscan_bottom=60 # padding from the bottom
# if using nano
# CTRL - X
# Y
# PRESS ENTER
# done. If error, then close file and run with sudo
sudo reboot now # then view screen, test and adjust accordingly
```

SCRIPTING
```bash
# use 2 greater then symbols to use a new line, and use 1 to truncate
sumeetsingh@Sumeets-Air-2 sandbox % echo '#!/bin/zsh' > test.sh && echo 'figlet HELLO WORLD | lolcat' >> test.sh
sumeetsingh@Sumeets-Air-2 sandbox % chmod a+rwx test.sh
sumeetsingh@Sumeets-Air-2 sandbox % ./test.sh
 _   _ _____ _     _     ___   __        _____  ____  _     ____  
| | | | ____| |   | |   / _ \  \ \      / / _ \|  _ \| |   |  _ \ 
| |_| |  _| | |   | |  | | | |  \ \ /\ / / | | | |_) | |   | | | |
|  _  | |___| |___| |__| |_| |   \ V  V /| |_| |  _ <| |___| |_| |
|_| |_|_____|_____|_____\___/     \_/\_/  \___/|_| \_\_____|____/ 
```

CRON JOBS
```bash
cat << 'EOF' > /path/to/test.sh # 1. Write script
#!/bin/bash
echo "Hello, this is a test script executed by cron job" >> /path/to/test.log
EOF

chmod +x /path/to/test.sh # 2. make script executable

# export EDITOR=nano  # Set your preferred editor (nano, vi, etc.)
crontab -e << 'CRONJOB' # 3. add new cron job
# Example: Run test.sh every day at 9 AM
0 9 * * * /path/to/test.sh
CRONJOB

crontab -l # 4. verify cronjob

crontab -e # 5. reschedule job
```


UNZIPPING
```bash
unzip vosk-model-small-en-us-0.15.zip
```

## NETWORKING

FIND ALL OPEN PORTS
```bash
netstat -tuln

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN         
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 :::445                  :::*                    LISTEN     
tcp6       0      0 :::139                  :::*                    LISTEN     
udp        0      0 0.0.0.0:37819           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 192.168.0.255:137       0.0.0.0:*                          
udp        0      0 192.168.0.211:137       0.0.0.0:*                          
udp        0      0 0.0.0.0:137             0.0.0.0:*                          
udp        0      0 192.168.0.255:138       0.0.0.0:*                          
udp        0      0 192.168.0.211:138       0.0.0.0:*                          
udp        0      0 0.0.0.0:138             0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 :::546                  :::*                               
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::36174                :::* 
```

OPEN PORT 21 - INSTALL FTP
```bash
sudo apt install vsftpd
sudo nano /etc/vsftpd.conf
Uncomment local_enable=YES # to allow local users to log in.
Uncomment write_enable=YES # to allow write access to the FTP server.
netstat -tuln # check if port now open
sudo systemctl restart vsftpd # then restart service and view port 21 now available for FTP
pi@retropi:~ $ tcp6       0      0 :::21                   :::*                    LISTEN 
```

RENEW/RELEASE IP
```bash
sudo dhclient # RENEW ALL DHCP LEASES
sudo dhclient -r # RELEASE
sudo dhclient -r wlan0 # CHOOSE INTERFACE
```

RESTART NETWORKING SERVICE
```bash
sudo systemctl restart networking
sudo systemctl restart dhcpcd
```

CLEARING ARP
```bash
arp -d *
```

USING NMAP
```bash
winget install nmap # windows
sumeetsingh@Sumeets-Air ~ %brew install nmap # mac

sumeetsingh@Sumeets-Air ~ % nmap -n 192.168.0.211
Starting Nmap 7.95 ( https://nmap.org ) at 2024-06-29 16:48 AEST
Nmap scan report for 192.168.0.211
Host is up (0.0055s latency).
Not shown: 996 closed tcp ports (conn-refused)
PORT    STATE SERVICE
21/tcp  open  ftp
22/tcp  open  ssh
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 1.26 seconds
sumeetsingh@Sumeets-Air ~ % 
```

FIND MAC - USING IP
```bash
sumeetsingh@Sumeets-Air ~ % arp 192.168.0.211
retropie.modem (192.168.0.211) at b8:27:eb:ba:19:85 on en0 ifscope [ethernet]
```


FIND MAC - FROM LOCALHOST
```bash
sumeetsingh@Sumeets-Air ~ % arp -a
? (169.254.169.254) at (incomplete) on en0 [ethernet]
? (192.168.0.0) at ff:ff:ff:ff:ff:ff on en0 ifscope [ethernet]
mymodem.modem (192.168.0.1) at a4:91:b1:c9:dc:c on en0 ifscope [ethernet]
? (192.168.0.2) at (incomplete) on en0 ifscope [ethernet]
? (192.168.0.11) at (incomplete) on en0 ifscope [ethernet]
lifx-color-668f14.modem (192.168.0.14) at d0:73:d5:66:8f:15 on en0 ifscope [ethernet]
? (192.168.0.18) at 1c:f2:9a:5a:36:3 on en0 ifscope [ethernet]
? (192.168.0.20) at 7c:b3:7b:6e:c1:fd on en0 ifscope [ethernet]
? (192.168.0.21) at (incomplete) on en0 ifscope [ethernet]
google-nest-mini-3.modem (192.168.0.23) at f8:f:f9:97:a3:c4 on en0 ifscope [ethernet]
google-nest-mini.modem (192.168.0.63) at d4:f5:47:41:be:5c on en0 ifscope [ethernet]
sumeets-air-2.modem (192.168.0.110) at 14:7d:da:27:c7:85 on en0 ifscope [ethernet]
sumeets-pc.modem (192.168.0.115) at 14:18:c3:9e:3c:d9 on en0 ifscope [ethernet]
lifx-color-66967c.modem (192.168.0.116) at d0:73:d5:66:96:7d on en0 ifscope [ethernet]
espressif.modem (192.168.0.155) at 94:3c:c6:da:4:cc on en0 ifscope [ethernet]
? (192.168.0.187) at e0:9f:2a:e6:60:50 on en0 ifscope [ethernet]
retropie.modem (192.168.0.211) at b8:27:eb:ba:19:85 on en0 ifscope [ethernet]
```

DOWNLOADING
```bash
curl -O https://alphacephei.com/vosk/models/vosk-model-small-en-us-0.15.zip
```


## HARDWARE

FIND ATTACHED USBS
```bash
pi@retropie:~ $ lsusb
Bus 004 Device 003: ID 0781:55b1 SanDisk Corp. SanDisk 3.2 Gen1
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05ac:0267 Apple, Inc. Magic Keyboard A1644
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

FIND ATTACHED HARDWARE | DRIVERS | KERNELL MESSAGES
```bash
dmesg
dmesg -w # for listen for new prompts
dmesg | grep usb # to filter for specific things
```

MOUNT STORAGE DRIVE | USB
```bash
# 1. When a storage drive is connected to a linux computer, it will either appear under. If the below entries are empty the device needs to be mounted first.
ls /mnt
ls /media

# 2. Run code below to find mounts
pi@retropie:~ $ lsblk
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda           8:0    1 233.1G  0 disk
└─sda1        8:1    1 233.1G  0 part
mmcblk0     179:0    0  29.2G  0 disk
├─mmcblk0p1 179:1    0   512M  0 part /boot/firmware
└─mmcblk0p2 179:2    0  28.7G  0 part /

# 3. We can see under ```/sda/sda1``` there is the unmounted USB storage. To mount first create a directory for it, then mount the unmounted drive to it
sudo mkdir /mnt/romusb
pi@retropie:~ $ sudo mount /dev/sda1 /mnt/romusb
pi@retropie:~ $ ls /mnt/romusb
 ROMS  'System Volume Information'

# 4. To make a mount persistent across reboots first find the storage media id
pi@retropie:~ $ sudo blkid
/dev/mmcblk0p1: LABEL_FATBOOT="bootfs" LABEL="bootfs" UUID="91FE-7499" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="4c3c1c9b-01"
/dev/mmcblk0p2: LABEL="rootfs" UUID="56f80fa2-e005-4cca-86e6-19da1069914d" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="4c3c1c9b-02"
/dev/sda1: LABEL="SanDisk" UUID="2C5B-D063" BLOCK_SIZE="512" TYPE="exfat" PARTUUID="c3072e18-01"

# 5. Edit the fstab file to input the UUID of the storage edia
pi@retropie:~ $ sudo nano /etc/fstab

proc            /proc           proc    defaults          0       0
PARTUUID=4c3c1c9b-01  /boot/firmware  vfat    defaults          0       2
PARTUUID=4c3c1c9b-02  /               ext4    defaults,noatime  0       1
# a swapfile is not a swap partition, no line here
#   use  dphys-swapfile swap[on|off]  for that
UUID=2C5B-D063 /mnt/romusb exfat defaults,nofail 0 0 # <- here is where we put the UUID of the SanDisk storage media above

```

# SCRIPTS

CRON JOB 1 - On low disk usage or high CPU/MEMORY usage alert
```bash

```

CRON JOB 2 - Restart critical services
```bash

```

CRON JOB 3 - Force change old passwords
```bash

```

CRON JOB 4 - Scheduled shutdown
```bash

```

---
title: "Getting Ubuntu to work on RB110"
date: 2014-02-03
forum: General Help
---

### Post by h.hittini on 2014-02-03
Hello everyone,

I'm not an expert and I may have included unnecessary steps but I just wanted to share how I could get Ubuntu Server 10.04 to work on my RB-110 [http://www.roboard.com/RB-110.htm](http://www.roboard.com/RB-110.htm) because I didn't find much support for the board
I chose this version because it is supported until April, 2015 which works fine with me

[COLOR=#800000] The guide will cover[/COLOR]
1) Installing Ubuntu Server 10.04 LTS
2) Getting Ethernet to work
3) Getting Wireless to work

[COLOR=#800000] Requirements:[/COLOR]
1) RoBoard RB-110 Single Board Computer
2) RoBoard Mini-PCI WiFi Card for RB-100
3) RoBoard Cables for RB-110
4) MicroSD Card
5) VMware Workstation
6) SD Card Reader
7) ubuntu-10.04.4-server-i386.iso[CENTER]
[SIZE=5][COLOR=#800000]Installing Ubuntu Server 10.04 LTS[/COLOR][/SIZE]
[/CENTER]
We will install the OS to the MicroSD using VMware Workstation on the laptop, do some modifications and then insert the MicroSD card in RB-110's MicroSD card slot; I used a SanDisk Ultra microSDHC 16G and it worked fine for me. In addition, I used VMware work station 9.0.0 build-812388
Please notice that I'm using Windows 7, so, if you have a different system you may find some differences 
1) Connect your card reader to the laptop, install drivers if needed and insert the MicroSD card to the card reader
I suggest disconnecting any other USB storage devices to avoid writing on them by mistake
2) Go to "My Computer", find your MicroSD and it's Drive Letter (F for example)
3) Right click on "My Computer" then click "Manage" then "Disk Management" on the left
4) You'll see all the drives connected to your computer, find drive letter corresponding to your MicroSD, you can use the capacity to double check that it's the right one. Now find the disk ID fir that drive, it's written to the left, in my case it's called "Disk 1"; check the attachment "disk_id"
5) Go to VMware Workstation, then file, then new virtual machine and configure the settings as follows
What configuration do you want:    Custom (Advanced)
Harware Compatibility:                  Workstation 9:0
Install from:                                I will install the operating system later
Guest operating system:               Linux                                               Version:          Ubuntu
Virtual machine name:                  ubuntu_microsd
Number of processors:                  2                                              Number of cores:         2         <<<you can choose whatever you want here
Memory for the Virtual Machine:     1GB                                                                              <<<you can choose whatever you want here
Network connection:                    Use bridged networking
SCCI Controller:                           leave it as recommended
Disk:                                          Use a physical disk (for advanced users)
Device:                                       PhysicalDrive1 (because my disk ID was disk 1)    Usage: Use entire disk
Disk File:                                     leave it as it is
Click Finish
6) Go to VM and then Settings
7) Go to Hardware --> CD/DVD (IDE) --> Connection --> Use ISO imagr file --> Browse --> Open the download Ubuntu (ubuntu-10.04.4-server-i386.iso)--> click OK
8) "Power on" the ubuntu_microsd virtual machine and install Ubuntu, leave everyithing as default but when you reach the "Software Selection" enable the "OpenSSH server" because we are gonna need it
9) When the installtion is complete you can use Putty to SSH to your virtual machine if you are don't feel comfortable typying inside VMware Workstation; the machine will have your laptop's IP address. This step is not importent, you can skip it.
10) Run the following commands
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-generic aptitude
```
I installed "linux-image-generic" because "linux-image-generic-pae" was installed by default and it doesn't work on the board
11) Use the following command to check the installed kernel version; mine was 2.6.32-55-generic
```
aptitude show linux-image-generic
```
12) Run the following and replace 2.6.32-55-generic with what you got in the previous step
```
sudo update-initramfs -k 2.6.32-55-generic -c
sudo update-grub
```
13) 
```
sudo reboot
uname -r
```
this should show you the kernel you are running and it should say "2.6.32-55-generic" or whatever you downloaded, BUT without pae suffix 
14) Congratulations, now you can connect the MicroSD card to the board and use Ubuntu but Ethernet is not working yet. I suggest going through the next part and then run the MicroSD card on the board
[CENTER][COLOR=#800000][SIZE=4]
[SIZE=5]Getting Ethernet to work[/SIZE][/SIZE][/COLOR]
[/CENTER]
You will need an internet connection to accomplish this goal, so I strongly recommend running Ubuntu on the MicroSD card through VMware Workstation, you will need to transfer the attached file r6040_source.zip to your MicroSD card. I uploaded the file to my Dropbox, then right click and "Share Dropbox Link", then used "wget LINK" in Ubuntu where LINK is the link I got from Dropbox
1) Run the following to get the necessary packages and unzip the driver
```
sudo apt-get install unzip linux-headers-2.6.32-55-generic gcc build-essential
```
```
sudo unzip r6040_source.zip -d /usr/src
```
2) Compile the driver and install it using the following, replace "2.6.32-55-generic" with the kernel you have
```
sudo -i
cd /usr/src/r6040
make -f Makefile-2.6 KDIR=/usr/src/linux-headers-2.6.32-55-generic
insmod /usr/src/r6040/r6040.ko
cp r6040.ko /lib/modules/`uname -r`/kernel/drivers/net/
ls /lib/modules/`uname -r`/kernel/drivers/net/
```
You should see "r6040.ko" after typing the previous command
```
sudo depmod -a
lsmod
```
Now you should see the module r6040 on the lef column
3) Do the following to be able to connect using the module and to load it at startup
```
nano -w /etc/network/interfaces
```
and replace eth0 by eth1, if you wanted to access the internet later using VMware change it back to eth0
```
nano -w /etc/modules
```
add "r6040" to the bottom line
4) Power off now and insert the MicroSD card to the board, If you have a VGA card connect it to find your IP address, use your router's home page to see the LAN Clients and find the address otherwise
After finding the IP address you should be able to SSH to the board

[CENTER][SIZE=5][COLOR=#800000]Getting wireless to work[/COLOR][/SIZE]
[/CENTER]
Now it's time to go wireless, if you bought the "RoBoard Mini-PCI WiFi Card for RB-100" you can follow these instructions to get it to work, it has vt6655 chipset BTW
1) Get the from here [http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/VIA-VT6655-series-Driver-13.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/OTHER-NETWORK-CARDS/VIA-VT6655-series-Driver-13.shtml)  to your board and then run the following
If the file was deleted I can email it for you, just let me know
```
unzip vt6655_win_driver.zip
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd win_driver
sudo ndiswrapper -i VNWL.inf
ndiswrapper -l
```
you should now see driver present. hardware present
```
sudo modprobe ndiswrapper
```
2) Run the following to make the module load by default on startup
```
sudo nano -w /etc/modules
```
add ndiswrapper to the bottom line
```
sudo reboot
```
3) "iwconfig" should show wlan0 now
4) You can follow this guide to connect the the access point [http://www.youtube.com/watch?v=qVqkldgPjjo](http://www.youtube.com/watch?v=qVqkldgPjjo)
If you needed more information or the guide didn't work for you type "man iwconfig" to see the complete manual

If you needed extra help let me know
Best of luck

[COLOR=#800000]References:[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1052426&page=3](http://ubuntuforums.org/showthread.php?t=1052426&page=3)
[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)
[http://forums.trossenrobotics.com/tutorials/how-to-diy-128/howto-configure-onboard-ethernet-in-ubuntu-904-linux-for-roboard-3278/](http://forums.trossenrobotics.com/tutorials/how-to-diy-128/howto-configure-onboard-ethernet-in-ubuntu-904-linux-for-roboard-3278/)

---


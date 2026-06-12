---
title: "Need help installing network adapter drivers"
date: 2013-02-25
forum: General Help
---

### Post by Nikle on 2013-02-25
Alright so i decided to try and use ubuntu for a while and it feels enjoyable, but i cant seem to install my adapter drivers properly. Im completely new to linux and i would love your help. Here's what the "readme" included in the disc says. I tried following the steps but somehow i end up having to install something using aptitude(?) and for that i need internet, which i don't have without the drivers. Perhaps you could simplify the followed instructions some more for me.




[CENTER]
RT5592 Linux Driver quick start		

====================
Check tools:  

====================
*Before install driver, please check already install compile tool and  kernel source code

1>Install compile tool
    $yum install gcc-c++

2>check kernel source code exists /usr/src/kernels/ "kernel name"

    Download your kernel source code
    *[http://www.kernel.org/pub/linux/kernel/](http://www.kernel.org/pub/linux/kernel/) 		
	or
    $yum install kernel-devel



====================
Build Instructions:  

====================
1> $tar -jxvf DPO_GPL_RT5592STA_LinuxSTA_vx.x.x.x.tar.bz2
     go to "DPO_GPL_RT5592STA_LinuxSTA_vx.x.x.x" directory.
    


2> In Makefile
	 
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 
     define the linux kernel source include file path LINUX_SRC
	 
     modify to meet your need.


3> In os/linux/config.mk 
	
     define the GCC and LD of the target machine
	
     define the compiler flags CFLAGS
	
     modify to meet your need.
     ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   	   
         => $wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
     ** Build for being controlled by WpaSupplicant with Ralink Driver
	   
         Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   
         => $wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make			
	
     # compile driver source code, need administrator.
	
     # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	 
        => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $make install
     #install driver
     #copy RT2860STA.dat to /etc/Wireless/RT2860STA/RT2860STA.dat

6>$vi /etc/rc.d/rc.local
     #input "ifconfig ra0 up"
    $reboot

7> unload driver    
    
     $ifconfig ra0 down

     $rmmod rt5592sta


[/CENTER]

---

### Post by seraphDev on 2013-02-25
How old is the machine you're on?  Do you know who makes your ethernet adapter?  You are either going to have to do these builds manually by downloading from another machine, or figure out your adapter issue.  Can you give a few more technical specs on your hardware?

---

### Post by grahammechanical on 2013-02-25
I have never needed to do any of that crazy stuff. Linux has many drivers built into the kernel. What disk are you getting that information from?

Is it not possible for you to connect this machine to the router/modem by a cable? Then you can open Additional Drivers and that utility will install the driver for you. It is a wireless adapter we are talking about?

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

You should also confirm that you can get an internet connect from a live session. If so then the driver package is on the Ubuntu CD/DVD.

Regards.

---

### Post by Nikle on 2013-02-26
Sorry for lacking some information and the delay of my reply. Here are my specs:

CPU: Intel i7-3770 3.40GHZ
Graphics card: Gainward 670GTX
Power unit/storage/supply: Silver power 650W
Hard-drive: Seagate Barracuda 1TB
Motherboard: MSI B75MA m-ATX

The wireless adapter: ASUS PCE-n53

Im using dual boot and windows is my prime OS. I just recently downloaded ubuntu 12.04 from the web.

The CD i got the information on is the one i got with my purchase. Its called

"ASUS Wireless
User Manual
& Utility Software
PCE-N53
Wireless-N PCI-E adapter

Hopefully this information is what you needed. Also this computer is very new and i use it mostly for gaming. (Will be doing other stuff on ubuntu).

---

### Post by Nikle on 2013-02-26
Im not the only one using the internet in my house and im upstairs while the modem is downstairs.

So no wired connections.

---

### Post by twinturbotom on 2013-02-26
I'm a noob with different yet troublesome hardware as you.  My reply may not be exactly what you need but may provide you with an idea of the process to follow:
the wiki has great info, for me it was [this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

in short, after liveCD install I had no wireless.  
1. I downloaded some "fwcutter" package (some sort of special un-archiving utility for this discussion) and a packed set of firmware /drivers.  
2. Put that on a USB stick to transfer to my non net connected machine
3. Installed cutter Ns used it to unpack firmware
4. Installed / moved extracted data to the firmware location Ubuntu looks for that sort of thing
5. Checked / unchecked drivers in additional drivers of system settings / updates dialog


I'm away from machine and a noob so this isn't exact or even the right thing for you.  More an overview of the process I used to fix a similar issue.  That wiki page should help you more.  Good luck!  Once you get the web and things working ubuntu will get addicting!  It's stellar!

---

### Post by 3rdalbum on 2013-02-26
It looks like your card is fairly new, and the driver has just missed out on being included in 12.10.

Without any kind of internet connection you're snookered from the start. Can you tether your mobile phone or use a different wifi device or something?

You'll need to install the "linux-headers-generic" and "build-essential" packages either using Ubuntu Software Center or by typing this command:

```
sudo apt-get install linux-headers-generic build-essential
```

Download and unpack the driver so it appears as a folder.

In the terminal, do the following:

```
cd <drag the folder to the terminal>
make
sudo make install
```

The last step will ask for your password; type it in and hit Enter. It won't display your password or any * characters as you type.

I'm assuming that all the extra stuff described in the instructions is unnecessary, because I've never had to do this extra stuff before.

After the "sudo make install" bit has finished, reboot.

When Ubuntu 13.04 comes out you'll probably find you won't need to do a thing, it'll all just work out-of-the-box.

---

### Post by Nikle on 2013-02-26
i cant seem to get this working. I tried downloading the stuff from my laptop on windows and putting it over, but installing packages seems impossible. 13.04 comming this year?

---

### Post by liutszho on 2013-05-11
13.04 is out and after install this card doesn't seem to be recognized or get wifi anymore. I came from 12.04 and did the make, make install steps and it was fine.

Now when I do the make install. I get this error.

make -C /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt5592sta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
make: *** [install] Error 2

---

### Post by lalaland on 2013-05-29
> **liutszho said:**
> 13.04 is out and after install this card doesn't seem to be recognized or get wifi anymore. I came from 12.04 and did the make, make install steps and it was fine.

Now when I do the make install. I get this error.

make -C /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux -f Makefile.6 install
mkdir: cannot create directory ‘/etc/Wireless’: File exists
make[1]: Entering directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
rm -rf /etc/Wireless/RT2860STA
mkdir /etc/Wireless/RT2860STA
cp /home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/RT2860STA.dat /etc/Wireless/RT2860STA/.
install -d /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5592sta.ko /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/
install: cannot stat ‘rt5592sta.ko’: No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/liutszho/Downloads/Linux/DPO_GPL_RT5592STA_LinuxSTA_v2.6.0.0_20120326/os/linux'
make: *** [install] Error 2


I'm did the same build a moment ago. Also am 'upgrading' from 12.04 ...
Looks like make install didn't find the rt5592sta.ko file. Did the make fail?
I noted make fails unless run make as su. 

Worked for me on 13.04 AMD64 server install
Afterwards 
modprobe rt5592sta.ko
check with iwconfig
then ifup ra0

and I'm using it right now...

---


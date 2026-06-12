---
title: "Help With Stuff After Install"
date: 2007-03-21
forum: General Help
---

### Post by ghost2332 on 2007-03-21
I am completely new to Linux and just installed Ubuntu onto another partition on my dell laptop. I am having trouble setting things up such as the video card, wireless card, multimedia stuff. For example, when trying to install what the wiki suggested for unlocking audio and video formats this is what I'm looking at in the Terminal(the first bunch of stuff is the command I got from the Wiki):

~$  sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I tried using easyubuntu for these things but when I try to run it from applications menu, nothing happens. I thought it might be a bad installation or something I might have screwed up so when I tried to reinstall it, a window came up saying:

Only one sotware management tool is allowed to run at the same time
Please close the other application e.g. 'Update Manager', 'aptitude' or 'Synaptic' first.

When I look at the system manager I don't see any of these applications running.
So basically I'm pretty lost on how to install things like drivers and what I talked about above. Any suggestions?

---

### Post by taurus on 2007-03-21
Post the output of this command from a terminal here.

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by ghost2332 on 2007-03-21
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  147 ?        00:00:00 kseriod
  188 ?        00:00:00 pdflush
  189 ?        00:00:00 pdflush
  190 ?        00:00:00 kswapd0
  191 ?        00:00:00 aio/0
  192 ?        00:00:00 aio/1
  824 ?        00:00:00 kirqd
 1682 ?        00:00:00 ata/0
 1683 ?        00:00:00 ata/1
 1688 ?        00:00:00 scsi_eh_0
 1690 ?        00:00:00 scsi_eh_1
 1779 ?        00:00:00 khpsbpkt
 1787 ?        00:00:00 khubd
 1800 ?        00:00:00 knodemgrd_0
 1874 ?        00:00:00 kjournald
 1960 ?        00:00:00 logd
 2106 ?        00:00:00 udevd
 2887 ?        00:00:00 kpsmoused
 2905 ?        00:00:00 shpchpd
 3190 ?        00:00:00 hda_codec
 3420 ?        00:00:00 mount.ntfs-3g
 3732 tty1     00:00:00 getty
 3733 tty2     00:00:00 getty
 3736 tty3     00:00:00 getty
 3737 tty4     00:00:00 getty
 3738 tty5     00:00:00 getty
 3739 tty6     00:00:00 getty
 3992 ?        00:00:00 acpid
 4089 ?        00:00:00 syslogd
 4115 ?        00:00:00 dd
 4117 ?        00:00:00 klogd
 4196 ?        00:00:00 dhclient3
 4215 ?        00:00:00 gdm
 4216 ?        00:00:00 gdm
 4233 tty7     00:04:39 Xorg
 4249 ?        00:00:00 cupsd
 4270 ?        00:00:00 hpiod
 4273 ?        00:00:00 python
 4325 ?        00:00:00 dbus-daemon
 4340 ?        00:00:06 hald
 4341 ?        00:00:00 hald-runner
 4347 ?        00:00:00 hald-addon-acpi
 4353 ?        00:00:00 hald-addon-keyb
 4373 ?        00:00:00 hald-addon-stor
 4395 ?        00:00:00 avahi-daemon
 4396 ?        00:00:00 avahi-daemon
 4417 ?        00:00:00 perl
 4456 ?        00:00:00 ondemand
 4495 ?        00:00:00 hcid
 4503 ?        00:00:00 sdpd
 4515 ?        00:00:00 krfcommd
 4549 ?        00:00:00 atd
 4562 ?        00:00:00 cron
 4662 ?        00:00:00 x-session-manag
 4697 ?        00:00:00 ssh-agent
 4700 ?        00:00:00 dbus-launch
 4701 ?        00:00:00 dbus-daemon
 4703 ?        00:00:00 gconfd-2
 4706 ?        00:00:00 gnome-keyring-d
 4709 ?        00:00:01 gnome-settings-
 4718 ?        00:00:00 sh
 4719 ?        00:00:00 esd
 4726 ?        00:00:17 metacity
 4731 ?        00:00:07 gnome-panel
 4733 ?        00:00:04 nautilus
 4737 ?        00:00:00 bonobo-activati
 4739 ?        00:00:00 gnome-volume-ma
 4746 ?        00:00:00 gnome-vfs-daemo
 4754 ?        00:00:00 evolution-alarm
 4765 ?        00:00:01 beagled
 4769 ?        00:00:00 gnome-cups-icon
 4774 ?        00:00:00 gnome-power-man
 4783 ?        00:00:00 trashapplet
 4808 ?        00:00:00 mapping-daemon
 4826 ?        00:00:00 mixer_applet2
 4833 ?        00:00:00 gnome-netstatus
 4891 ?        00:00:01 gnome-screensav
 7574 ?        00:00:00 easyubuntu
 7575 ?        00:00:00 gksu
 7576 ?        00:00:00 python
 7583 ?        00:00:00 sh
 7584 ?        00:00:00 dpkg
 7585 ?        00:00:00 frontend
 7599 ?        00:00:00 flashplugin-non
 8358 ?        00:00:59 gaim
11902 ?        00:00:08 firefox-bin
12003 ?        00:00:00 gnome-terminal
12005 ?        00:00:00 gnome-pty-helpe
12006 pts/0    00:00:00 bash
12025 pts/0    00:00:00 ps

I think I'm more confused now lol.

---

### Post by taurus on 2007-03-21
You need to close down easyubuntu and anything else (like synaptic or whatnot) first before running these two commands from a terminal.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ghost2332 on 2007-03-21
Ok so I even reset my laptop and then made sure nothing was running in the system but I still got all this:

```
001:~$ sudo aptitude update
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]                      
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                    
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US             
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US           
Get:2 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US            
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com edgy Release                                
Hit http://us.archive.ubuntu.com edgy-updates Release                           
Hit http://us.archive.ubuntu.com edgy/main Packages                             
Hit http://us.archive.ubuntu.com edgy/restricted Packages                    
Hit http://us.archive.ubuntu.com edgy/universe Packages                      
Hit http://us.archive.ubuntu.com edgy/multiverse Packages                    
Hit http://us.archive.ubuntu.com edgy/main Sources                           
Hit http://us.archive.ubuntu.com edgy/restricted Sources                     
Hit http://us.archive.ubuntu.com edgy/universe Sources                       
Hit http://us.archive.ubuntu.com edgy/multiverse Sources                     
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                  
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages            
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages              
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com edgy-updates/main Sources                   
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources             
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources               
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources             
Err http://security.ubuntu.com edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
99% [Connecting to security.ubuntu.com (82.211.81.138)]
99% [Connecting to security.ubuntu.com (82.211.81.138)]^[[B^[[B^[[B[3~
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Fetched 2B in 3m37s (0B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache

```

And then:
```
001:~$ sudo aptitude upgrade
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

Could it be something that I messed up elsewhere when I was looking around at the repository stuff?

---

### Post by taurus on 2007-03-21
Did you try to install flash plugin but somewhere didn't quite finish?  From a terminal, run

```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ghost2332 on 2007-03-21
Yes, I think that was one of the things that got messed up actually, good call. I ran the first line of code you gave me and it threw some more errors at me :) 

```
:~$ sudo dpkg --configure -a
Password:
Setting up flashplugin-nonfree (9.0.21.78~ubuntu1~edgy1) ...
Downloading... download failed
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree

```

---

### Post by hikaricore on 2007-03-21
Probably not the solution you want, but I believe:

```
sudo apt-get remove flashplugin-nonfree
```

Will _probably_ do the trick.

I've had to do this manually a few times by editing the dpkg file. >.<

---

### Post by ghost2332 on 2007-03-21
I think that worked :D, thanks for the help. Now how do I put it on there the right way? Do I run the upgrade and update commands from above and then enter that other stuff in?

---

### Post by hikaricore on 2007-03-23
You could just download it from adobe and install with their installer:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Uncompress this file and run the installer program from a terminal window.

This will automatically install with no need to mess with any packages.

Though I don't usually suggest installing without a package manager, there's
no sense in sending you off on a mission to rebreak your dpkg and apt-get lol.

---


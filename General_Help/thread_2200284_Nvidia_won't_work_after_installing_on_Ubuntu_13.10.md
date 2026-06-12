---
title: "Nvidia won't work after installing on Ubuntu 13.10"
date: 2014-01-18
forum: General Help
---

### Post by rfr2 on 2014-01-18
Hello.

I am having a hard time installing nvidia drivers on my ubuntu 13.10. I am trying to run a steam game (Dota 2) but it runs on very very low fps. After plenty of research I've found out that I may require to install some additional drivers. Said and done I quickly updated from the update center and rebooted. Couldn't start ubuntu anymore (black screen). Reinstalled it, googled about how to install nvidia from terminal... (sudo apt-get install nvidia-current) didn't work... 

Downloaded drivers manually, stopped lightdm, installed with sudo sh nvidia..blabla... reboot. Still doesn't work, sitting on the same black screen. Tried another approach: 

sudo apt-get purge nvidia*

sudo apt-get install nvidia-current

still doesn't work


another approach

sudo apt-get purge nvidia*
sudo apt-get linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings

... 

I am running a GTX 570... I can't get ubuntu to load after I installed the drivers. 

Reinstalled ubuntu after each black screen... 

Please assist.

---

### Post by grier-devon on 2014-01-18
When you say "update center" do you mean "software & updates"? When you go in there do you have the proprietary drivers or the open source drivers enabled.

---

### Post by rfr2 on 2014-01-18
> **grier-devon said:**
> When you say "update center" do you mean "software & updates"? When you go in there do you have the proprietary drivers or the open source drivers enabled.


yes you are right, it's called software and update center. where can I see if they are enabled or not?

---

### Post by jeanjd63 on 2014-01-18
Hello 

Can you give the return for :
**sudo  lspci  -vnn  |  grep  -i vga**

---

### Post by rfr2 on 2014-01-18
> **jeanjd63 said:**
> Hello 

Can you give the return for :
**sudo  lspci  -vnn  |  grep  -i vga**

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF110 [GeForce GTX 570 Rev. 2] [10de:1086] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:1571]
    Subsystem: eVga.com. Corp. Device [3842:1571]

---

### Post by jeanjd63 on 2014-01-18
You can try this :
1) install nvidia drivers :
**sudo  apt-get  install nvidia-current [COLOR=#000000]nvidia-settings[/COLOR]**
2) create the file xorg.conf :
**sudo  nvidia.xconfig**
3) restart the computer.
If you got a black screen, you open a console : CTRL+ALT+F1 , log you and do :
**startx**
and give the returns

---

### Post by rfr2 on 2014-01-18
will do this very quickly, please stay @ !

---

### Post by rfr2 on 2014-01-18
will do this very quickly, please stay @ !

edit: my first answer in terminal

 sudo nvidia.xconfig
sudo: nvidia.xconfig: command not found

---

### Post by jeanjd63 on 2014-01-18
You have first do this ? :
**sudo apt-get install nvidia-current [COLOR=#000000]nvidia-settings[/COLOR]**

---

### Post by rfr2 on 2014-01-18
yes, sudo apt-get install nvidia-current nvidia-settings
[sudo] password for rff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot nvidia-304 nvidia-settings-304 python-xkit
  screen-resolution-extra
Suggested packages:
  dpkg-dev debhelper
The following NEW packages will be installed:
  dkms fakeroot nvidia-304 nvidia-current nvidia-settings nvidia-settings-304
  python-xkit screen-resolution-extra
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 70,1 MB of archives.
After this operation, 210 MB of additional disk space will be used.
Do you want to continue [Y/n]? y


edit: also

ls -l
total 48
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Desktop
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Documents
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Downloads
-rw-r--r-- 1 rff rff 8980 ian 18 16:46 examples.desktop
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Music
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Pictures
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Public
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Templates
drwxr-xr-x 2 rff rff 4096 ian 18 17:07 Videos
-rw-r--r-- 1 rff rff    2 ian 18 19:32 xorg.conf

---

### Post by sdowney717 on 2014-01-18
[http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

I use the xorg edgers PPA

> ```
sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install <package name>
```

after you do update, then you should see this new listing for nvidia drivers.
I use synaptic to install most things. not software center.

sudo apt-get install synaptic, then run synaptic and search for nvidia

---

### Post by jeanjd63 on 2014-01-18
And now :
[B]sudo  nvidia.xconfig
[/B]doesn't work ?

---

### Post by rfr2 on 2014-01-18
> **sdowney717 said:**
> [http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

I use the xorg edgers PPA



after you do update, then you should see this new listing for nvidia drivers.
I use synaptic to install most things. not software center.

sudo apt-get install synaptic, then run synaptic and search for nvidia


ok should I purge the nvidias I just installed now, get the edgers ppa and then install synaptic?

> **jeanjd63 said:**
> And now :
[B]sudo  nvidia.xconfig
[/B]doesn't work ?

still command not found :'(

---

### Post by sdowney717 on 2014-01-18
> **rfr2 said:**
> ok should I purge the nvidias I just installed now, get the edgers ppa and then install synaptic?

Only if you cant get it to work.

the nvidia drivers need a nvidia config file to run, AFAIK, that is why the sudo command suggestion, but maybe now automatic.

here are more instructions. for me was painless.

[http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml)

[QUOTE]```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
```

once it is going with this ppa, they send out new updates for drivers and it is pretty simple.

you can log into a console window, at boot up. 
Does grub give you a boot menu? 
then you can run these commands, you should not need to reinstall the os.

---

### Post by rfr2 on 2014-01-18
> **sdowney717 said:**
> [QUOTE=rfr2;12903825]ok should I purge the nvidias I just installed now, get the edgers ppa and then install synaptic?

Only if you cant get it to work.

the nvidia drivers need a nvidia config file to run, AFAIK, that is why the sudo command suggestion, but maybe now automatic.

here are more instructions. for me was painless.

[http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml](http://news.softpedia.com/news/How-to-Install-the-Latest-NVIDIA-331-20-Drivers-in-Ubuntu-13-10-399182.shtml)



once it is going with this ppa, they send out new updates for drivers and it is pretty simple.

will do this real quick and restart

---

### Post by rfr2 on 2014-01-18
Okay sorry for posting after myself. I just run what sdowney717 told me to in terminal... I ended up with the black screen again T_T 

had to reinstall ubuntu... this is why it took me so long. 

Please someone assist me on this.

---

### Post by sdowney717 on 2014-01-18
What is the screen monitor your using?


There is a log file for xorg called Xorg.0.log
'EE' shows errors, 'WW' warnings.
It should describe the error after you install the driver, should show up and tell you more info

look in /var/log/ in the file system, it also has old logs, but if your wiping the system clean then that will all be gone.
Somehow you need a failsafe boot menu to view the log. Or even pull the drive and view it somewhere else.
Or you can boot up the USB install and view it. you might need to chroot into the drive.

sample of mine
```
[    20.494] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    20.494] X Protocol Version 11, Revision 0
[    20.494] Build Operating System: Linux 2.6.24-29-xen x86_64 Ubuntu
[    20.494] Current Operating System: Linux scott-P5QC 3.12.0-031200-generic #201311031935 SMP Mon Nov 4 00:36:54 UTC 2013 x86_64
[    20.494] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.12.0-031200-generic root=UUID=c78457d6-e870-4a34-ac83-13535294ec4a ro quiet splash
[    20.494] Build Date: 09 July 2012  05:20:18PM
[    20.494] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support) 
[    20.494] Current version of pixman: 0.30.2
[    20.494] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    20.494] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.494] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 17 23:51:55 2014
[    20.614] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.683] (==) No Layout section.  Using the first Screen section.
[    20.683] (==) No screen section available. Using defaults.
[    20.683] (**) |-->Screen "Default Screen Section" (0)
[    20.683] (**) |   |-->Monitor "<default monitor>"
[    20.683] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    20.683] (==) Automatically adding devices
[    20.683] (==) Automatically enabling devices
[    20.745] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.745] 	Entry deleted from font path.
[    20.745] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.745] 	Entry deleted from font path.
[    20.745] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.745] 	Entry deleted from font path.
[    20.745] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
```

---

### Post by sdowney717 on 2014-01-18
A few ideas, I have set up multiple drives in a PC, I have even run ubuntu from a usb external drive. If you have a working install you can view files on an drive in the system easily.
Maybe set up on a second drive to view the log on a failed install.

---

### Post by oldfred on 2014-01-18
Did you originally install from nVidia and not from repository?
If so you have to thoroughly houseclean as they otherwise conflict.

Otherwise process is the same as you have done.

I think this was only required for 12.10, and is not needed for your version, but will not hurt to check. Headers are needed for updates.
 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

Check what versions are offered, but you must install the same settings version also.
apt-cache search nvidia

       
 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

---

### Post by rfr2 on 2014-01-19
> **oldfred said:**
> Did you originally install from nVidia and not from repository?
If so you have to thoroughly houseclean as they otherwise conflict.

Otherwise process is the same as you have done.

I think this was only required for 12.10, and is not needed for your version, but will not hurt to check. Headers are needed for updates.
 # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

Check what versions are offered, but you must install the same settings version also.
apt-cache search nvidia

       
 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

I have just tried what oldfred told me. I did not get a black screen anymore after reboot !

this is what I get now

root@rfr:/home/rfr# lspci | grep VGA -i
01:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 570 Rev. 2] (rev a1)



I will install the game again and see how it runs, will keep you guys updated so you can mark this thread as _solved_. Cheers!

Also a question for those who know, will I get a black screen after next kernel update? or do I need to update anything anymore???

 I am really looking forward to seeing how the game will respond and how much fps I'll have.

PC specs : 16gb ram, 570gtx nvidia, i7

---

### Post by rfr2 on 2014-01-19
Thank you very much for your support. The game runs even smoother than on windows. Thanks again, I hope we can assist each other in the future with any issues we encounter.

You can mark this thread as [SOLVED].

Cheers again!

---

### Post by oldfred on 2014-01-19
If you install from nVidia directly, you have to manual reconfigure for each kernel update as it is integrated into the kernel. 
If from repository, then it is automatic and you should not have any issues.

With a nVidia card I find I have to use nomodeset on every install ISO, on first boot or until I install nVidia from repository.
I normally suggest only using repository, unless you happen to have a very very new card that version in repository does not handle. But Ubuntu has been better at updating repository so usually it has very current versions from nVidia.

---


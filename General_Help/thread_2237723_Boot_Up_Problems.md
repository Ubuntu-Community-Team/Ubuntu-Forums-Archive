---
title: "Boot Up Problems"
date: 2014-08-03
forum: General Help
---

### Post by cpl3043usmc on 2014-08-03
Good afternoon from rural northwestern Virginia, everyone!

I have been encountering a problem during the boot up sequence with my laptop.  But first, I have searched through the forums and run searches on Google looking for similar issues and help.  There are a few people out there with similar problems, but what helped them isn't working for me.  I've already updated the stacks and run autoremove and autoclean, as well as making regular checks and updates to the system.  I have also run a memtest which showed no errors.

Second, my laptop's specs: I am using an Acer Aspire TimelineX 4830TG-6450.  It has an Intel Core i5 2.4GHz processor, 8GB DDR3 RAM (upgraded from 4), and a 250GB SSD (upgraded from 640GB HDD, which took a dump on me).  I'm running 12.04 LTS and recently upgraded the HWE stack to 3.13.0-32-generic (which, coincidentally, is about the time the boot problems started).

Now for the problem: Recently, during boot up, I've been having trouble getting past the boot up/log on screen.  Sometimes a message pops up very briefly that mentions something about mounting and gives options to do something but it disappears immediately to a black screen... and then nothing.

Restarting my laptop will bring it to the log on screen, but the keyboard and touch pad are non-responsive, and the cursor just sits in the password entry box.

Restarting a third time will bring me to the log on screen, with the same problems as the second time, but now the bongos/drums/whatever start up sound effect just plays over and over and over... and over.... and I'm forced to restart a fourth time.

On the fourth restart, everything works fine.  I'm able to log on, the desktop loads up, and it's all rainbows and unicorns.

Has/is anyone else experiencing this problem?  If so, how did you fix it?

---

### Post by cpl3043usmc on 2014-08-03
Follow up:

Part of the problem may have been my NVIDIA driver (331-upgraded).  I noticed something about NVIDIA in a screen that popped up and disappeared rathr quickly during a restart.  I removed the driver and restarted my laptop.  So far, so good.

---

### Post by cpl3043usmc on 2014-08-05
I was wrong.  I'm still experiencing problems with booting up my laptop.

The message on the Ubuntu start up screen says something about a /crypt-something , but that message disappears very quickly.  It has something to do with mounting.  I'm not sure what's going on, but it's starting to get a bit frustrating.  

To make matters worse, whatever is happening is also affecting other operations of my computer: connecting to my WiFi, starting applications, keeping applications functioning -- they either display "Not Responding" or just shut down and restart...

... I'm really hoping that my laptop is not failing hardware-wise.  

Just in case, I'm performing a back up of all my data to my desktop.  I've got all of my grad school work on this laptop, I can't afford to lose it.  I can't really afford a new laptop, either, but I will be less upset buying a new laptop than I would trying to replicate all of my thesis work.

---

### Post by cpl3043usmc on 2014-08-05
Another update:

Something called Compiz is constantly failing.  I am given the option of sending a report, than it prompts me to choose a means of finding a way to correct the error.

---

### Post by cpl3043usmc on 2014-08-05
Another update:

The laptop is back to restarting itself.  I have performed an update and done and autoremove/autoclean.  Now I see a screen before the laptop reboots and it mentions a lot of things failing and uses Xorg a lot.

---

### Post by cpl3043usmc on 2014-08-06
Final update:

I was able to get my laptop to load up to the desktop, and have it operate long enough to remove the NVIDIA 331-upgraded driver.  

Searching through the various Ubuntu forums and help guides had me changing settings, installing programs, editing *.conf.* files and various other tricks to try and get something working that just doesn't want to work.

I'm hoping to get things working one last time so I can put my information on a flash drive and save my thesis.

Thanks for the wild ride, Ubuntu.  It was well timed.

---

### Post by oldfred on 2014-08-06
Do you have dual video or are you using the open source version?

I would look in the log files for issues.
I first look in /var/log/dmesg

You may have log file viewer or just open it.

        
 gksudo gedit /var/log/dmesg
    

You want to look for outright errors, repeated tries at loading a driver and either sucess later or failure. And any entries with long differences in the timestamps. Not sure if it is the first or second entry when large difference is shown.

I just noticed I seem to have an issue, but did not notice that boot was that slow?

```
[    8.904875] init: udev-fallback-graphics main process (966) terminated with status 1
[  165.936907] kjournald starting.  Commit interval 5 seconds
[  165.937155] EXT3-fs (sdd6): using internal journal

```

In my case the fallback graphics has an error as only status 0 is ok.

And then next timestamp is 165. Not sure if fallback was slow ending or the journald had issues on sdd6? Off to do some checks.

---

### Post by cpl3043usmc on 2014-08-06
Thanks for the reply, oldfred.

I'm currently trying to reinstall ubuntu... well, actually, kubuntu 14.04 LTS.  Ubuntu 12.04 and 14.04 won't load to the desktop, even when just trying to "try it" from the USB drive.  I get the "Ubuntu" with dots and that's it.  I'm going to see if KUbuntu 14.04 is any better.

My laptop does have the dual graphics nonsense that I've been reading about for the past day.  It seems that Ubuntu (or Linux in general) and NVIDIA don't like each other much.  Regardless, I have the integrated Intel graphics as well as a NVIDIA GT540M.  Something isn't talking inside this machine, I just don't know what.  I was able to get to the command line and copy my /home/<name> directory, so I saved my thesis, research files, STATA files, etc.  So I can continue my work from my desktop.

The interesting thing, my wife also has an Acer laptop but her's isn't experiencing the same problems.  She has a different model, so I'm assuming a different graphics card as well.  She's been running Ubuntu 12.04 and hasn't encountered anything like what I'm dealing with.

I have no logs to check because I can't get the laptop to display anything anymore.

---

### Post by oldfred on 2014-08-06
Some systems let you control which video mode you are in.

With nVidia you need nomodeset. But Intel may need other boot parameters depending on a variety of factors which I do not fully understand. ubfan1 documented most of those. Some systems also require other boot parameters.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. If UEFI you get grub menu or after install you need to add boot parameters until proprietary drivers are installed.

How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


Vendors often have similar issues across models. Not sure if anyone posted what you may need or not.
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by cpl3043usmc on 2014-08-07
Thanks for the info, oldfred.

I was able to get KUbuntu 14.04 loaded and logged on via the terminal.  (I didn't even let it get to the initial graphics.)  I found some help here:
[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

I was able to get everything going through the terminal, restarted my laptop, and so far KUbuntu 14.04 is running without any problems.

For anyone else who reads this:  I did try to reinstall Ubuntu 12.04.  I also tried to install 14.04.  Both seemed to lag really, really bad.  I don't know if it's my laptop or not.  It's a few years old, but I don't think that's the issue.  Regardless, I like the look and feel of KUbuntu.

Again, oldfred, thanks for the help!

---


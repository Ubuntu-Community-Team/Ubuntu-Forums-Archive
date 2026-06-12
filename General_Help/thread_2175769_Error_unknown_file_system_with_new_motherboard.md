---
title: "Error: unknown file system with new motherboard"
date: 2013-09-20
forum: General Help
---

### Post by catnip-gn on 2013-09-20
Using 13.04 ubuntu.  Got a new motherboard and at first startup my /home partition was not able to be mounted.  Rebooted and now the error I get is error: unknown file system then goes to grub rescue.  

Thought I'd try live cd only it gets to the Ubuntu splash screen and hangs there.  Various configs in bios, used other hard drives, and still same result with live cd.  What am I not doing right?

---

### Post by VMC on 2013-09-20
Are the hard drives you are using from the old motherboard? If so, then maybe check if you have correct drivers for the new board.

---

### Post by dcstar on 2013-09-20
Check AHCI or RAID settings in the BIOS, turn them back to IDE if you can and see if that helps.

Check the RAM to make sure it is functioning without errors with MEMTEST.

---

### Post by catnip-gn on 2013-09-22
Yes, same hard drives from the old motherboard.  Not quite sure how to load new, correct drivers when I'm having issues with getting anything to boot up correctly.

I did upgrade the BIOS, but same issue.

---

### Post by catnip-gn on 2013-09-22
i was able to set it to native IDE, but still nothing.
I did notice one thing though - UEFI and Legacy boot options.  I have it set to UEFI AND LEGACY - would this change anything?

---

### Post by oldfred on 2013-09-22
Old drives probably would be legacy. New system will be UEFI with BIOS compatibility mode (CSM) so it should boot in BIOS mode. But you have to choose that from UEFI menu.

What video are you now using, Intel internal or new video card? That may make for issues.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

How new is system? Some Haswell with internal video need other settings also.

---

### Post by catnip-gn on 2013-09-22
only did legacy and helped dvd drive but not the hd.  No onboard video, using video card from other mobo.  Did f6 option,  used nomodeset and gets me to Ubuntu desktop but freezes there now.

---

### Post by philo565 on 2013-09-22
Now that you can at least get to the desktop...that's good. If your system is locking up, it could be video related. Are you using the same video card as was in your old system, if not you may have to reconfigure from safe boot.
VIZ: If you had the nVidia drivers installed and are now using a non-nVidea card for example

---

### Post by catnip-gn on 2013-09-22
yes, same video card as in other system.   Right when the Ubuntu desktop appears,  system freezes, no keyboard or mouse usage.   
How do I go about resolving a driver issue if I can't get to desktop?

---

### Post by philo565 on 2013-09-22
Since you are using the same video card then it is probably not a video driver problem.
You can open a terminal by hitting  control-alt F4 and log in from there. You can still use  sudo apt-get to uninstall packages such as your nVidia driver then retest.
Linux usually reconfigures itself pretty well to new H/W but it's possible you will need to reinstall

---

### Post by catnip-gn on 2013-09-22
I can't even get to a terminal. .. The system is dead once the desk top m appears.   Should I just install new and point home directory to the right partition?

---

### Post by philo565 on 2013-09-22
Before you install new, try the recovery option from your grub menu ...there is a failsafe video mode you can try.

Otherwise I'd be sure your data are backed up. If you do a re-install, be sure to keep your /home partition intact.

---

### Post by catnip-gn on 2013-09-22
negative on the grub menu options....goes straight to grub rescue

---

### Post by catnip-gn on 2013-09-23
ok.  Not sure what to do next.  After install hanged,  I decided o move usb keyboard and mouse to usb 3.0 connections.  got my mouse and kb to work this way,  but not able to install...Does not see my hard drive nor anything connected via usb 2.0

---

### Post by philo565 on 2013-09-23
I can't offer much help at this point. It might be a BIOS setting of some sort, such as perhaps having legacy USB turned off.
I'd try a live cd from some other version of Linux...or use a spare HD and see if you can install another OS entirely just to confirm the mobo is actually good.

---

### Post by oldfred on 2013-09-23
I cannot offer anything more either. 
Most users have issues with USB3 ports and have to use USB2.

Is this an Asrock MB? The Asmedia ports can cause issues.
Other motherboards do often need specific settings that often are hard to figure out as they may not seem to apply.
Users have posted these:
 Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.
Changed IDE Mode to AHCI Mode
Then,when the SATA3G_1 selection appears in the drive list below,select the Enabled option.
set pci=nomsi or other boot paramater

Laptop but some Intel unrelated setting

 Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.

---

### Post by catnip-gn on 2013-09-24
so I finally got it to see my hd and went for new install with keeping my /home directory.   Only It kept defaulting to format my /home directory,  which I do not want.   No matter what I tried,  it would self check the format box after I would set it up without format. 

it is amd processor with gigabyte mobo 970A-d3p i think.... got sent out of town and can't exactly recall the model #.

But the usb 2.0 not working is perplexing,  while the only slot that does is 3.0

---

### Post by dcstar on 2013-09-26
> **philo565 said:**
> Since you are using the same video card then it is probably not a video driver problem.
........

Putting the same Video card in different hardware invariably means that the xorg.conf settings will now be wrong and it **will** cause problems.

Do a search on replacing the xorg.conf file with a default file and then reinstall the video hardware driver to configure the new setup.

---

### Post by catnip-gn on 2013-10-05
would fixing this xorg solve my grub rescue issue?  Also,  can I fix xorg during try ubuntu before install?

---

### Post by catnip-gn on 2013-10-05
So do I have two, seperate issues here?  For one - grub isn't loading and the second, my video settings are not working correctly?  

When I look at the hard drive using ls commands after grub rescue - I get (hd0), (hd0,msdos1), (hd0,msdos2), (hd0,msdos3).  When I look at each individual hd0 using ls hd0,msdos#/ - i get nothing.  

I suppose once (if) I get grub to load correctly, I can tackle the video settings.

---

### Post by VMC on 2013-10-05
grub listing is done this way:
grub> (hd0,1)/<directory>/<directory>/<etc>
For example:
```
(hd0,1)/boot
```

edit: I don't recall you giving us the boot info. Download bootinfoscript (mybluelink) , and copy it back here between "[CODE]" tags.

---

### Post by catnip-gn on 2013-10-06
I tried running under su and sudo with livecd
bash: syntax error near unexpected token 'newline'

let me run this again...I think I know my error

---

### Post by catnip-gn on 2013-10-06
Well...I gave up.  I backed up my home directory to another hard drive and went for a fresh install.  everything works, except the darned USB 2.0 ports.  I selected the USB Legacy and made this Enabled, which was previously on Auto.  Still nothing.  I'm going to play around with BIOS settings tomorrow and if I don't get it working, i'm getting a new motherboard.  

I appreciate everyone's assistance.

---

### Post by VMC on 2013-10-07
Look at the output of ```
lsusb
```, if all you usb devices show up, then open a terminal (Ctrl+Alt+t) and type the following and then plug in the usb device to see what messages *syslog* shows:```
tail -f /var/log/syslog
```.
You could just look at *syslog* directly, but this way you see immediately what happens when you plug in the device.
 When finished viewing for any failed message, type 'Ctrl+c' to exit. 

Also typing '*dmesg*' into a terminal might reveal something.

---

### Post by catnip-gn on 2013-10-07
read/64 error,  -110 is what in get.

---

### Post by catnip-gn on 2013-10-08
Well....here I am using my new motherboard.  After some searching within Ubuntu forums, I found my issue with the USB 2.0.  For any future reference, within BIOS - enable the IMMOU.  
Now the odd thing is - my USB 3.0 doesn't work.  :^(

I'll play around with this a little more.

Now going to work with video settings to get that item squared away.

So I backed up my /home directory to a separate hard drive.  What's the easiset way to recover that?

---

### Post by oldfred on 2013-10-08
You can just copy everything back, or mount the /home if a permanent drive from your install.
Some of the copy commands using rsync.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---


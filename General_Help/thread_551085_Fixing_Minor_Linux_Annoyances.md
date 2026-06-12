---
title: "Fixing Minor Linux Annoyances?"
date: 2007-09-14
forum: General Help
---

### Post by Dylnuge on 2007-09-14
I have a few problems which, while not essential to be fixed, I would like to deal with.

1. My laptop won't switch from LCD to CRT output and back when I press Fn + F8. I instead must manually restart the GDM with Ctrl + Alt + Backspace. When I do this, if it detects the projector, it only will output in CRT-I must be staring at the projector to use the laptop, which is not good when I need to do something for setup and don't need it broadcasting.

2. CD's won't eject with the button on my tray. I must right click on the CD icon and tell it to eject, or else I get an error saying that the media cannot eject. If this is a safety feature, I would like to disable it-I know when I can and cannot eject a disk. The tray works fine for ejection when there is no disk.

3. Sound seems much softer then on Windows. Not a huge problem, but can become an issue when I want to listen to something. This includes when I am hooked into speakers, headphones, or even surround sound systems. I know they can go louder then this, so it must be the software sending the sound-namely GNOME. Any fixes are appreciated.

4. Acrobat will only open one PDF at a time (outside of Firefox). I like it better than any of the document viewers, but I wish I could open more windows. I believe it can do this on Windows.

Thanks to anyone who helps,
Dylan

---

### Post by Dylnuge on 2007-09-15
Help with any one of these would be appreciated.

Thanks,
Dylan

---

### Post by eggdeng on 2007-09-15
I hope some of the following suggestions may be of use.

Sound issue: Run ```
alsamixer
``` in a terminal and adjust your settings. If you don't have alsamixer installed, run ```
sudo apt-get install alsamixer
``` (The linux sound server is OSS, not Gnome).

CD issue: Linux distros require you to unmount the file system before you eject the CD. In this case, the system knows better than you.

Acrobat issue: You can open several documents simultaneously by using the Cascade option in the Window menu. & I agree with you that Adobe have done a 1st class job.

---

### Post by Dylnuge on 2007-09-15
All right, thanks, this is helpful.

First, alsamixer already has master set to 100. What do the other values do?

I knew that ALSA (OSS) was the sound server, just wasn't thinking. ;). Thanks for the help on acrobat-works great now! Still hoping to get the presentation stuff working, and now Update Manager is crashing the system!

Thanks,
Dylan

---

### Post by eggdeng on 2007-09-15
> First, alsamixer already has master set to 100.
Make sure you have PCM  turned up all the way too.
> What do the other values do?
I don't honestly have much of an idea.:)

---

### Post by Dylnuge on 2007-09-16
Great, thanks! System sounds great now.

Still having problems with Update Manager, though. I will try Synaptic-I know install works fine, but I want to see if update works.

---

### Post by Dylnuge on 2007-09-16
Synaptic won't work either anymore! It does not crash the system, it just does not start. I get this error:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Running the mentioned command gives this:

```
dpkg: error processing xchat-common (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of xchat:
 xchat depends on xchat-common (= 2.8.4-0ubuntu4~feisty1); however:
  Version of xchat-common on system is 2.8.4-0ubuntu2~feisty1.
dpkg: error processing xchat (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xchat-common
 xchat
```

This is almost certainly due to the fact that the update was interrupted because the system crashed. The Update Manager was having problems before-I originally thought they were related to the kerberos libraries, which I still have not updated.

Aptitude works, but it is crazy. It, for some reason, recomends that I remove a bunch of software I use a lot, including acetoneiso2, kchmviewer, quanta, and some stuff I have never heard of, like libpaper and exaile. What's odd, however, is that all of these changes are listed under unchanged, and mentioned in the information that their dependancies remain unchanged. For example, quanta is mentioned both by cervisia and kompare. Both state that the following actions will resolve the dependency of quanta requires (cervisia/kompare) by removing quanta, keeping (cervisia/kompare), and leaving the dependancy unresolved. This is extremly confusing. Please help!

---

### Post by Steveway on 2007-09-16
1. Should be fixed with Xorg 7.3
4. How about epdfviewer, I like it.

---

### Post by Dylnuge on 2007-09-16
4 was already fixed, but thanks Steveway, especially for the info on Xorg. As for my package problem,. I kind of got around it:

Used aptitude. Cancled all of the suggested changes, uninstalled xchat and xchat-common, reinstalled xchat and xchat-common, upgraded kerberos libs. Everything went smoothly. Synaptic works again.

Okay, I have answers to everything now. Thanks for all the help!

EDIT: Actually, I am still interested in the CD issue. I know the FS needs to be unmounted first, but doesn't Linux do this automatically? The error is that it could not unmount, not that I need to unmount, and CDs used to eject without a problem.

---

### Post by Dylnuge on 2007-09-17
Anyone know anything about the CDs?

---

### Post by tgalati4 on 2007-09-18
>sudo apt-get remove xchat

That should fix the update manager.  You can then reinstall xchat if you use it.  Or don't if you don't use it.

>sudo apt-get install xchat

>sudo eject /dev/cdrom

or

>sudo eject /dev/cdrw

or 

>sudo eject /dev/dvd

These devices are normally automounted and autounmounted, but there are situations that can cause problems.  For instance loading a Data CD into the CDROM will mount it as a folder.  If you are browsing that folder then hit the physical eject button on the CDROM, you will get an error:  "Can't unmount, Device Busy".  This is because you are still browsing it.

If you are playing a music CD (commercial or burned) and hit the eject button, I believe it will just unmount it.

It's different behavior from Windows, and there is a reason for it.

---

### Post by Dylnuge on 2007-09-18
Thanks for the info, tgalti, but I already fixed the packages (the remove xchat stuff).

As for the ejection, every cd refuses to automount. I don't need to use the terminal, I can just right click and choose eject, but it would be nice if I could just press the button. Every CD gives the same error:Cannot eject volume. Cannot eject volume: DISKNAME, with DISKNAME being replaced by the disk's label.

Now I got a new error message. I have never seen this one before:
```
Failed to eject "/org/freedesktop/Hal/devices/storage_model_DVD_RW_TS_L632D".
Given device "/org/freedesktop/Hal/devices/storage_model_DVD_RW_TS_L632D" is not  a volume or drive.
``` This occured on one disk, I am going to see if it happens on others. Oh, and once again, clicking eject in the options menu worked fine.

PS: Clearly something different then just autounmount not working is going on, at least for the error I just got. It says that HAL does not consider my CD Drive a drive.

---

### Post by strabes on 2007-09-18
The CD problem is fixed in gutsy.

---

### Post by Dylnuge on 2007-09-19
Good to know as well. Gusty is still on track for an October launch, right?

---

### Post by Dylnuge on 2007-09-29
Sorry to bump, but I just had a quick concern.

I know how to fix the sound issue now (move PCM to 100), but when I reboot, PCM goes back to 44. Is there anyway to make PCM automaticly and permanantly 100?

---


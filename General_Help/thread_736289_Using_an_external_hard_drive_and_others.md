---
title: "Using an external hard drive and others"
date: 2008-03-26
forum: General Help
---

### Post by jlpizzle on 2008-03-26
Well, I finally made the switch from Windows XP/Vista to Linux and I am currently using Gutsy Gibbon.  There are a few problems that I am running into that I could greatly use some assistance on.

1)  My external hard drive (My Book Essential 500GB) was my backup for my Windows XP laptop and I plugged it in using Linux and I cannot gain access to my files. I am at work atm so I can't tell you the exact message that was given.  Can someone please help me in gaining access to my drive again without losing all of the data.

2)  I have a Dell AIO 924 All-in-one printer and I need to figure out how to get the printer to work with Linux.

3)  What is the easiest and most appealling widget software for linux? gdesklet is the only one I have gotten so far, but haven't figured out how to get new widgets yet (granted I haven't spent too much time on this part).

4)  Lastly, for a beginner Is KDE easier to learn on or GNOME? Or is there even a difference or preferance?


Thanks for all the help I am going to receive.  I have heard that linux users provide the best in newbie helping. :D

---

### Post by jlpizzle on 2008-03-26
BTW, I have a Dell laptop (Inspiron 9300) which now cannot control my sound using the hardware buttons.  AND even when I am controlling the mater volume via software, I can't go completely mute.

---

### Post by warp99 on 2008-03-26
> 1) My external hard drive (My Book Essential 500GB) was my backup for my Windows XP laptop and I plugged it in using Linux and I cannot gain access to my files. I am at work atm so I can't tell you the exact message that was given. Can someone please help me in gaining access to my drive again without losing all of the data.

Need more information when you plug the drive in. When you get a chance plug the hard drive in, then go to a console and type the following:

```
dmesg |tail 
```

and post the contents to this thread

> 2) I have a Dell AIO 924 All-in-one printer and I need to figure out how to get the printer to work with Linux.

That printer my friend is a re-branded Lexmark and unfortunately a paperweight according to OpenPrinting.org:

[http://openprinting.org/printer_list.cgi?make=Dell](http://openprinting.org/printer_list.cgi?make=Dell)

My suggestion would be to get an HP printer because they are supported very well in Linux. So before you buy a printer check with OpenPrinting.org for compatibility.

> 3) What is the easiest and most appealling widget software for linux? gdesklet is the only one I have gotten so far, but haven't figured out how to get new widgets yet (granted I haven't spent too much time on this part).

Gdesklet is the one that I would use since it does integrate well with Gnome. If you are using KDE 3.5.x then Superkaramba would be your choice, until KDE 4.1 is released some time in June, very impressive.

> 4) Lastly, for a beginner Is KDE easier to learn on or GNOME? Or is there even a difference or preference?

You can install both desktops on your machine to check them out. All you have to do is load the kubuntu-desktop:

```
sudo apt-get install kubuntu-desktop
```

Here are some more instructions with screen shots at this link:

[http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html](http://www.debianadmin.com/install-kde-desktop-in-ubuntu.html)

Then when you are at your login screen choose the KDE session instead of the Gnome session to access that desktop. You can check out both and pick the one that feels the most comfortable. I prefer KDE, but I don't want to start a desktop flame war. :)

---

### Post by warp99 on 2008-03-26
> **jlpizzle said:**
> BTW, I have a Dell laptop (Inspiron 9300) which now cannot control my sound using the hardware buttons.  AND even when I am controlling the mater volume via software, I can't go completely mute.

You can do this:

> In Ubuntu with a GNOME desktop go to:

 * System->Preferences->Keyboard Shortcuts

 * Pick a random action, such as Home folder by clicking once on the Disabled text.

 * Press the hotkey

 * Disabled should now be replaced with the magic number of the hotkey, such as 0x9f.


If that doesn't work you can always put in a bug report at the following link:

[https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch](https://wiki.ubuntu.com/LaptopTestingTeam/HotkeyResearch)

---

### Post by jlpizzle on 2008-03-26
Thanks Warp99. I'll get right on that when I get home.

---

### Post by jlpizzle on 2008-03-26
The message reads...

Cannot Mount volume.
Unable to mount the volume 'My Book'

Details: $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action:

  Choice 1: If you have Windows...... (Don't have windows anymore)
  Choice 2: If you don't have windows then you can use the 'force' option for your own responsibility for example type on the command line:  mount-t ntfs-3g/dev/sdb1/media/My Book-o force    

   OR add the option to the relevant row in the /etc/fstab file:    /dev/sdb1/media/My Book ntfs-3g defaults,force 0,0.

At the moment, this is a different language to me.  What is the best course of action.

Again, thanks for the continuing help.

---

### Post by jlpizzle on 2008-03-26
jlpizzle@JDELL:~$ dmesg |tail
[113409.900000] usb 5-8: USB disconnect, address 11
[113413.928000] usb 5-1: USB disconnect, address 8
[113413.928000] usb 5-1.1: USB disconnect, address 9
[113413.928000] usb 5-1.2: USB disconnect, address 10
[113413.928000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: removed
[115636.000000] usb 5-8: new high speed USB device using ehci_hcd and address 12
[115636.132000] usb 5-8: configuration #1 chosen from 1 choice
[115636.132000] scsi5 : SCSI emulation for USB Mass Storage devices
[115636.132000] usb-storage: device found at 12
[115636.132000] usb-storage: waiting for device to settle before scanning
jlpizzle@JDELL:~$

---

### Post by warp99 on 2008-03-26
> **jlpizzle said:**
> The message reads...

Cannot Mount volume.
Unable to mount the volume 'My Book'

Details: $LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.  Choose one action:

  Choice 1: If you have Windows...... (Don't have windows anymore)
  Choice 2: If you don't have windows then you can use the 'force' option for your own responsibility for example type on the command line:  mount-t ntfs-3g/dev/sdb1/media/My Book-o force    

   OR add the option to the relevant row in the /etc/fstab file:    /dev/sdb1/media/My Book ntfs-3g defaults,force 0,0.

At the moment, this is a different language to me.  What is the best course of action.

Again, thanks for the continuing help.

The drive has been formatted for NTFS so you have to use the ntfs-3g to write to the drive because Microsoft is not very open with their specifications. Normally if the drive was formatted FAT32 then udev would have auto-mounted the drive. Now ubuntu tried to auto-mount the drive (dmesg |tail) but failed.

Now you can access the drive with the ntfs-3g drivers, but will need to mount the drive manually in order to write to the drive. Since the drive is not always attached to the notebook I would choose option 2. You can use a GUI utility called ntfs-config that will mount the drive when connected:

[http://packages.ubuntu.com/gutsy/ntfs-config](http://packages.ubuntu.com/gutsy/ntfs-config)

You can download the package by using the Synaptic package manager, but you need to enable the universe repositories. Open Synaptic and choose Settings > Repositories tick the box for the universe repository. Close then reload, scroll down to ntfs-config and install the application. 

I haven't used the program personally, but according to the ntfs-3g driver developers ntfs-config "is reported to work nicely on at least Ubuntu." I hope this answers your questions. ;)

---

### Post by jlpizzle on 2008-03-28
Thank you so much Warp99. After about an hour I was able to mount the drive and no problems since.

---

### Post by myfigurefemale on 2008-03-30
I have the same problem and the same error message.  NTFS-3G and NTFS-config didn't work for me.  Any suggestions?  I'm using an 80g "My Book" and need it work between both windows and linux, and can't reformat as all my data is backed up on it in NTFS format.

Thanks.

---


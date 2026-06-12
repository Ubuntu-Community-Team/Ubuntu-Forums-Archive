---
title: "running ubuntu 12.04 from usb memory in tandem with Windows 7"
date: 2014-02-27
forum: General Help
---

### Post by alopex38 on 2014-02-27
I've just purchased a new laptop [Toshiba Tecra ] and, for reasons irrelevant, am forced to live with Windows 7.  However, I bought a 4gb memory stick with Ubuntu 12.04 installed on it and would like to run ubuntu from my usb2 port [leaving Windows 7 in situ for my wife].

My question is how exactly do I do this - I love technology but it seems somehow to hate me!

I would be most grateful for any help on this matter. 

alopex38

---

### Post by monkeybrain20122 on 2014-02-27
Running off a usb flash drive is going to be painfully slow, I would suggest that you install instead in an external hard drive.

**Edited:**
Take a look at [http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
He did it for lubuntu 12.04  but for Ubuntu 13.10 it is more or less the same. He installed in a usb flash drive, but as noted it will be very slow so it is not practical to use. Get an external hard drive instead. The procedures are the same.

In the screen where it asks you to choose the way to install, choose "something else" then choose the external device (say /dev/sdc)

The thing to pay attention to is the bootloader installation. By default it will be installed in your internal hard drive, you don't want that. So in the drop down choose the external drive you want to install Ubuntu into (something like /dev/sdc) Some people suggest that you remove the internal hard drive first before installing but it is not necessary if you are careful at this point. I have done this many times, I never remove the internal hard drive.

**Edited again:** All these assume that you use old fashion BIOS (since it is a win7 machine) but if you have uefi then you'll need to do some modifications. No special insight there except to tell you to google because I have no experience with such machines.

---

### Post by ajgreeny on 2014-02-27
It will depend to some extent what you mean by "I bought a 4gb memory stick with Ubuntu 12.04 installed on it".

Was it a full install, which seems unlikey on 4GB, or is it a live USB system?
If you shutdown windows properly (not hibernate or suspend), insert the stick into the machine then power it on and hit the appropriate key to change boot priority device to your usb, you should end up with a running ubuntu OS with (probably) an icon on the screen or in the launchbar on the left side to "Install ubuntu 12.04".  That means it is a live USB system which you can run as it is, but all files made and changes you make will be lost on rebooting it.

You can dual boot most systems using windows 7 without too many problems, choosing from the grub menu which OS to boot to.  UEFI, instead of legacy BIOS,complicates things to some extent but Windows 7 may not use that so you could be in luck.

Start by booting to the USB as I say above and then we can go further with you if you wish to proceed to a full installation.

---

### Post by squakie on 2014-02-27
+1 on the size - it is really too small to do much of anything.  Also, you can actually install Ubuntu to a flash drive - different from having a "live media" where you used something like unetbootin to create the USB flash drive.  If you do want to use "just" the "live media", then indeed ajgreeny is correct that by the defaults in unetbooin you won't have any changes or additions saved if you reboot.  However, unetbootin does give you the options of "persistence" and offers that as a question of how big do you want the persitance file to be.  This is where the smaller size flash drive you are using could get you in trouble.  If you plan to really load a bunch of stuff in, keep a lot of docuemtns, etc., then you are going to need a large persistence file.  I would suggest a minimum of a 16GB flash drive and giving a persistence file size of 10GB (I'm not sure how big the install itself is).  This file will be used to "remember" any changes, additions, documents, music,etc., from 1 boot to the next.

If you need a 16GB flash but can't get one, let me know.  You would need to live in the U.S. before I can consider helping on that.  Such flash drives are available here at Micro Center for well under $20.

---

### Post by monkeybrain20122 on 2014-02-27
> **squakie said:**
> +1 on the size - it is really too small to do much of anything.  Also, you can actually install Ubuntu to a flash drive - different from having a "live media" where you used something like unetbootin to create the USB flash drive.  If you do want to use "just" the "live media", then indeed ajgreeny is correct that by the defaults in unetbooin you won't have any changes or additions saved if you reboot.  However, unetbootin does give you the options of "persistence" and offers that as a question of how big do you want the persitance file to be.  This is where the smaller size flash drive you are using could get you in trouble.  If you plan to really load a bunch of stuff in, keep a lot of docuemtns, etc., then you are going to need a large persistence file.  I would suggest a minimum of a 16GB flash drive and giving a persistence file size of 10GB (I'm not sure how big the install itself is).  This file will be used to "remember" any changes, additions, documents, music,etc., from 1 boot to the next.

If you need a 16GB flash but can't get one, let me know.  You would need to live in the U.S. before I can consider helping on that.  Such flash drives are available here at Micro Center for well under $20.

A live usb with persistence is still a live usb, it is not an installation into the usb drive as in the link I posted above.  And an installation into a flash drive would run very slow no matter how big it is because of the read/write speed, that's why i suggest an external hard drive instead.

---

### Post by ajgreeny on 2014-02-27
The largest you can make a persistence file on a live USB is only 4GB as a result of fat32 limitations on file-size; nothing to do with Ubuntu.

There is a way round that problem (see [http://ubuntuforums.org/showthread.php?t=2165496](http://ubuntuforums.org/showthread.php?t=2165496)) but in all honesty you would do far better to use a proper dual boot installation.  Even an external USB hard drive will still be very slow compared with a SCSI internal hard drive as a result of the limitation on transfer speeds of USB.  Maybe a USB-3 external drive would work but I have no experience of that so can not comment.

---

### Post by mastablasta on 2014-02-27
or you can use virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

and install it inside windows :-) much faster than dualboot.

or set aside a piece of hard disk and install ubuntu there for dualboot. set windows as first boto option in GRUB bootloader so that computer will automaticly boot to windows but if oyu want it ti can also boot to Ubuntu.

---

### Post by monkeybrain20122 on 2014-02-27
> **ajgreeny said:**
> The largest you can make a persistence file on a live USB is only 4GB as a result of fat32 limitations on file-size; nothing to do with Ubuntu.

Even an external USB hard drive will still be very slow compared with a SCSI internal hard drive as a result of the limitation on transfer speeds of USB.  Maybe a USB-3 external drive would work but I have no experience of that so can not comment.

No, the external hard drive is as fast as the internal one. I am using one with the exact set up as what OP wants right now. The computer is a borrowed one as mine is sitting broken in the repair store. It has Win 7 in the internal drive and I boot my own Ubuntu installation in an external drive. I have also had booted it off other computers, it is my portable Ubuntu, never noticed any speed difference.

---

### Post by monkeybrain20122 on 2014-02-27
> **mastablasta said:**
> or you can use virtualbox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

and install it inside windows :-) much faster than dualboot.



No way that VB would be be faster than dual boot. :) Moreover to run vb I would suggest at least 4 G of ram and VB doesn't handle 3d desktop gracefully so with VB unity or gnome shell is out of the question.

---

### Post by squakie on 2014-02-27
I whole heartedly agree.  I was only suggesting persistence if the OP wanted to keep with a "live media".  As far as speed - I know from personal experience that it is terrible.  If at all possible, it would be nice to have the OP dual-boot. An external drive is fine as long as it is always there (at least in my experience).  Grub can get a little weird when installed on the "normal" hard disk with another OS on an external disk - anyway for me (maybe I missed something).  BUT - ANYHTING is better than running off a flash drive!  I agree that if the user can't dual-boot with the internal drive (perhaps it's too small?) an external drive would be great.  The prices on them have really come down, and if all you want is 30 to 100 GB, you can pick up a used one ("refurbished" as they say at Micro Center) really cheap and the external case to connect it via USB is really cheap as well.  I don't worry about an externally powered case unless the drive is not a 2.5" laptop drive.

At any rate, I agree completely!  I was just suggestiog the persstence if they wanted to stay with a live media.  I tried installing to a USB flash drive a few times, and every time it was SO slow I couldn't stand it.  Wasn't even worth it just for testing.

There might also be an alternative, depending on the OP's hardware - installing Ubuntu in a virtual machine in Windows.

Dave ;)

---

### Post by monkeybrain20122 on 2014-02-28
> **squakie said:**
>   Grub can get a little weird when installed on the "normal" hard disk with another OS on an external disk - anyway for me (maybe I missed something).


It will get a little weird only if you install the bootloader in the internal hard drive. If that is the case you won't be able to boot without the external drive attached. But if you install the bootloader correctly in your external hd then there is nothing weird. See my last paragraph in my first edit in my post #2. 

The added bonus of installing in an external drive is that you can boot it off other machines as long as the hardware supports it (booting from external device and supporting Linux) and not just in the original machine, so it is portable. When I visit my family in another continent I don't even bring my laptop, just the external drive with a clone of my system to boot off my dad's Windows7 machine. When I detach the drive my dad boots into Windows just as usual, nothing weird and when I leave I bring the external drive with me back to Canada.

---

### Post by alopex38 on 2014-02-28
Many thanks to all who replied and for the useful feedback.  Looks like I will have to go down the "Virtualbox" route.

Cheers alopex38

---

### Post by monkeybrain20122 on 2014-02-28
> **alopex38 said:**
> Many thanks to all who replied and for the useful feedback.  Looks like I will have to go down the "Virtualbox" route.

Cheers alopex38

Not sure why "have to" , vb is not the optimal solution, far from it.

---

### Post by squakie on 2014-03-01
```
It will get a little weird only if you install the bootloader in the  internal hard drive. If that is the case you won't be able to boot  without the external drive attached. But if you install the bootloader  correctly in your external hd then there is nothing weird. See my last  paragraph in my first edit in my post #2. 

The added bonus of installing in an external drive is that you can boot  it off other machines as long as the hardware supports it (booting from  external device and supporting Linux) and not just in the original  machine, so it is portable. When I visit my family in another continent I  don't even bring my laptop, just the external drive with a clone of my  system to boot off my dad's Windows7 machine. When I detach the drive my  dad boots into Windows just as usual, nothing weird and when I leave I  bring the external drive with me back to Canada.                 
```Sure, but then there is making sure the person knows how to find either the boot menu or can go into each machine's BIOS and make sure USB is a boot option and if so that it is above the hard disk.  For a lot of users, that is beyond their grasp.

Hey, not trying to argue with you!

---

### Post by monkeybrain20122 on 2014-03-01
> **squakie said:**
> Sure, but then there is making sure the person knows how to find either the boot menu or can go into each machine's BIOS and make sure USB is a boot option and if so that it is above the hard disk.  For a lot of users, that is beyond their grasp.

Hey, not trying to argue with you!

What you say is very true, that's why I posted a link to amjjawad's tutorial, he has taken the trouble to show a lot of screenshots and photos from bios options, partitions to the installation process. It is the best guide for new users I can find (with trivial modifications for newer versions of Ubuntu)

---

### Post by squakie on 2014-03-01
Hey - if you "talk" with amijawad sometime, tell him the guy formerly known as "anewguy" says "hi!".  Haven't "talked" to him in ages!

---


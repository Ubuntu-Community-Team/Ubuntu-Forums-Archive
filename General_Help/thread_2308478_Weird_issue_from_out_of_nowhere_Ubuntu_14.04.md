---
title: "Weird issue from out of nowhere Ubuntu 14.04"
date: 2016-01-03
forum: General Help
---

### Post by ericj2 on 2016-01-03
Hi:

Fairly new to Ubuntu, but hae a handle on MS-DOS, Windows and seem to catch on fairly well.

Anyway  couple months ago or so I installed 14.04 on a desktop (I7) in a dual-boot with Win 7.

Got it done pretty smoothly with one or two questions to others, but it seemed to be working great until this morning. Last night when I shut it down it was fine, then this morning it seemed to hang up at the initial (hp BIOS) screen where you press ESC go go to the boot menus, etc. Stayed there for quite a while and I almost decided to hit the power button.

Finally after selecting Ubuntu from the boot menu the screen goes black for a second as usual... except much longer this time, then this error message comes up saying "USB 4-1.1 device descriptor read/64 error 110"

Finally it did boot up to the O.S. and that seemed to be working OK, but then I shut it down, pulled the plug for a few min. and rebooted... still doing the same weird thing taking several minutes to go through the boot.

Any ideas from the experts? I seem to be getting this "Minty" flavor in my mouth :)

Thanks.
Eric

---

### Post by brian-mccumber on 2016-01-03
I have read a couple places that sometimes Windows does not shut down all the way when you tell it to shutdown and it causes havoc with the boot procedure since Windows try's to retain ownership of hardware even tho it said it shutdown. It seems to go into some hybrid suspend mode instead of completely shutting down sometimes. I have also read that you can completely power the computer down i.e. pulling the power cord and holding power button then try to boot back up. If it's a laptop unplug the adapter remove battery and then hold the power button down for a few seconds then try to reboot.

---

### Post by ericj2 on 2016-01-03
I did cut the power and reboot, another weird thing is now text at least in firefox is different sizes than it was.

Thanks for the suggestion though

---

### Post by brian-mccumber on 2016-01-03
Maybe you accidentally zoomed your browser, try to press CTRL + 0 which is control plus zero to reset the zoom.

I have seen t0o many problems on this forum that stems from trying to dual boot with Windows, I don't think I would even try dual booting  seen to much bad crap about it. I really only need one operating system to do the type of work I do. If I absolutely needed to run Windows for a specific software or something I would use Wine or a dedicated computer and monitor for it running just Windows and another dedicated computer and monitor for Ubuntu or whatever other Linux distro I choose to use at the time and then use kvm switches so I can share keyboard and mouse. But anyway someone who knows more about this will probably come in here to help you, so good luck.

PS If your computer has a add on graphics card installing the proprietary graphics drivers for your card from Addition Drivers found by searching for drivers in your Ubuntu dash might alleviate some of the problems.

I don't think the Ubuntu devs are able to keep up with all this new hardware coming out that is so different from older hardware that used to just work out of the box. New drivers and supporting software have to be added to compensate for the fact that manufacturers don't mind breaking their consumers computers to try new technologies and hardware and there is no one to tell them they should follow a specific standard of manufacturing that would give all of us consumers a much better experience when trying to do crap like dual booting and other risky ventures.

---

### Post by ericj2 on 2016-01-03
I hesitated to dual boot but now have done it on 3 machines and working pretty well. I (unfortunately) need a few things I can only do on Windows and I once tried to install Wine but it didn't install right and the Win programs I need to use are not known to work in the Wine environment.

I'm running Linux Mint on one computer and may replace Ubuntu on here with that... maybe, but then I have to download the progs. I have installed again.... but might be worth it.

Thanks for trying to help, so far help has been very good here.

---

### Post by Geoffrey_Arndt on 2016-01-03
Just a couple thoughts:   

>  Ubuntu used to (about every 40 sessions or so),  run a script to check for hdd integrity.   Bootup during those times is slower than normal.    
>  Did you have a USB Flash-Stick, External HDD, or SD card inserted into a mmc or usb port of the PC?  Sometimes these devices can also cause issues (such as if one of them were used for backup, which had errors or if the device is full).

If neither situation applies, I would suggest also to check for system updates and run that through.   Also, you can use the "Disks" utility in Ubuntu for scan your system for early-stage errors.

---

### Post by brian-mccumber on 2016-01-03
What are the things that you have to use Windows for? Is it like Photoshop or Ms Office software? Adobe software and Microsoft office software seem to be the only things that keep alot of people from wanting to switch permanently. I had no problem with this at all, Gimp is just as good as PS to me, I learned on Gimp then got PS when I went to college but I didn't mind switching back to Gimp and Inkscape from PS and Illustrator. And I have found the opensource office software it just as good as MS, interfaces are a little different but the bulk of the features are included in both the opensource and proprietary office software suites available and they can both open and export each other's native file types. Lamp servers for php and web dev are much easier to get installed and working in Linux than Wamp servers in Windows and the way the Ubuntu file system integrates with ftp makes working on and uploading/swapping sites to new hosts a snap where it used to take multiple programs to do the same things in Windows I can do with just the Unity file manager. The only software I couldn't carry over or find an alternative to is MS Visual Studios but since then I figured out how to use gtk or glade to create guis for apps that can be written in c or c++ and there is a Ubuntu package that allows the use of Visual Basic if VB was the only language I could use and this new type of development is cross platform compatible where programs/software created with Visual Studios will pretty much only run on Windows. Eh sorry for the dump here but these are my thoughts on this and again good luck.

---

### Post by ericj2 on 2016-01-03
I do have a USB drive plugged in, but it has been the whole time and I actually did unplug it from the system when I rebooted after unplugging the computer and it still did the same thing, I'll see what other utilities are on my system.

---

### Post by Kris_M on 2016-01-03
I also dual boot with win7 and 14.04.3 Unity and have no probs with it.

I wondered "connection" but I don't know where your win7 partition is or your Linux partition is - both sata? both SSD? HDD? external USB stick?

Made me think your BIOS lost it a bit...

---

### Post by ericj2 on 2016-01-03
I have been using 2 Windows video editing programs for years Magix Movie Edit Pro, and Sony Vegas along with Adobe at times, also Magix  music maker. I have checked out Openshot, KDenlive, Pitivi, LMMS and either they crash repeatedly or can't do all the things I am used to. Also for webpages although I often hard code I also use Sitespinner and if I want to modify any of the projects I have designed using that it would be hard not to use it to change the project.

There are other things too, I have used Gimp for quite a while, it's OK. I hate Windows but as much as I don't like the fact there is just good software out there that I don't (yet) see a Linux replacement for.

I originally wanted to get away from Windows but I keep discovering reasons to use it now and then.

---

### Post by grahammechanical on 2016-01-03
There seem to be 2 or 3 problems here.

1) The BIOS is taking its time to load the Grub boot menu
2) Grub is taking its time to load Linux
3) This is getting in the way

> "USB 4-1.1 device descriptor read/64 error 110"

I suggest 2 things. In Ubuntu open a terminal and run

```
sudo update-grub
```

That will make sure the the boot menu is looking in the right places. Watch the printout to the screen. And if the USB is in the boot menu updating Grub with the USB removed will clear the USB out of the boot menu.

You may also want to check the BIOS settings to see if a USB drive is listed as first in priority. If there is something wrong with the USB drive then the BIOS will try again and again to load and fail each time and that prolongs the boot process. If Linux is having difficulty starting processes, it will try again and again. And all this prolongs the loading process.

Regards.

---

### Post by ericj2 on 2016-01-03
I ran the terminal update as you suggested, sounded like a good idea. Thanks!

I earlier checked for general updates using the usual software update and it came back as already up to date.

I'm not sure if I can get to the BIOS settings... in order to access the boot options on this you hit ESC when the initial screen opens, and I have tried that but only after the screen has been hanging for a bit. I will try it though.

Not sure you understood though (or maybe you did) , I am running both Ubuntu and Win7 off my hard drive, not off a USB drive.

I always hate to reboot when there are boot issues and the computer is otherwise working OK.... but I guess I should before long.

Thanks again all.

---

### Post by tripp98 on 2016-01-03
If your computer/motherboard has the ability to test the hard drive you may want to run diagnostics on it.  if grub takes a while to wake up where it was running fast previously then that is a sure sign of hard drive failure.

---

### Post by ericj2 on 2016-01-03
Yeah I think I can do that through Windows if I can get back there. I did a "self-test" using  the "disks" utility in Ubuntu and it seemed fine. Oddly after closing and opening Firefox a few times now the (tabs mostly) fonts look as they did before.

What's even weirder is I have several computers and being unconnected it's weird that it always seems I have an issue with one, then another ...

---

### Post by ericj2 on 2016-01-03
Well, I again tried to unplug/reboot after booting into Windows to see if I could find anything weird there. Everything seems to check out, it has to have something to do with the BIOS or something before any O.S. even loads. I don't know enough about what all goes on during a boot... at which point grub gets accessed, etc.

Tried going to BIOS last boot to see if settings looked OK but even though the initial screen stays up for a prolonged time, I could not get to any of the settings by hitting ESC as should work. It just hung up there, was real slow and then gave me the same error message. Hate to think about it but if I can't get to the BIOS settings I may soon have to take the machine to someone who knows more cause now not sure how I could install Mint (if that would even do anything) re-install Ubuntu or whatever without being able to alter the boot order. For now though, once I get past the weird boot issues everything seems fine.

---

### Post by Geoffrey_Arndt on 2016-01-04
Just in case you're not aware, but there are a couple possibilities:

1).   Often, the best way to run Windows programs in Linux is via a VM like VirtualBox,
2).   I frequently check this website for alternative software:  [http://alternativeto.net/](http://alternativeto.net/)

---


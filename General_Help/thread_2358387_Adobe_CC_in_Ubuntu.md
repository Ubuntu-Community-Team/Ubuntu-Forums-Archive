---
title: "Adobe CC in Ubuntu"
date: 2017-04-12
forum: General Help
---

### Post by thepentool on 2017-04-12
I'm a graphic designer, and I need to use various programs in Adobe's Creative Cloud (Illustrator mainly, but I use all of them to varying degrees) on a daily basis.  I really want to switch from Windows 10 to Linux, but the Adobe suite is a deal-breaker.  It's my livelihood, and dual-booting kind of defeats the point.  I want a true, clean Linux experience.

So is there any way to get full functionality from Adobe's Creative Cloud in Linux?  I don't mind if I have to run a VM (I have a legal copy of Windows 10 that I can use) inside of Linux, so long as the VM can actually run the suite properly.  

I've looked around Google, but keep running into the same old (and I do mean old) articles.  

Anybody have any experience with this?

Thanks!

---

### Post by Bucky Ball on 2017-04-13
Welcome. A VM should work fine. Consider it a regular Windows install, with a few caveats, but probably none that will effect what you're trying to do (do you use a Wacom tablet? ... test in Virtualbox to see if you can get that working). 

The main consideration is if you have the hardware to do it. The RAM is shared between the host OS and the guest OS, in your case, Ubuntu host and Win10 guest. Win10 is greedy and likes plenty of RAM (a resource hog all round actually). Graphic design, depending on what you're doing, can also be demanding. You would probably want 3 or 4Gb for the guest machine to start, but you can experiment and try lower. 

I suggest you install Virtualbox from the repositories, make a Win virtual machine and try it out, see how it flies. Tweak how much RAM you give it and see if you can make it fly. Adobe natively in Linux is not going to happen anytime soon, or probably anytime in my lifetime!, so VM is probably your only choice if dual-booting is out of the question. 

Hope that helps a bit and good luck with it. ;)

---

### Post by howefield on 2017-04-13
The alternative to a VM would be to use Wine, [https://appdb.winehq.org/objectManager.php?sClass=version&iId=33725](https://appdb.winehq.org/objectManager.php?sClass=version&iId=33725).

Realistically, the best bet is probably a Windows VM.

---

### Post by dragonfly41 on 2017-04-13
There is a useful list here ...

[http://www.creativebloq.com/productivity/free-alternative-adobes-creative-cloud-21514120](http://www.creativebloq.com/productivity/free-alternative-adobes-creative-cloud-21514120)

I would add ImageMagick and LaTeXDraw to the list of tools, depending on your needs.
Look also at Blender.

---

### Post by thepentool on 2017-04-13
Thanks for all the responses.  My concern with a VM is that the video card will still be limited.  Last time I used something like VirtualBox, there was no 3D support for video -- and things like video games (I'm a Skyrim addict) in a VM was laughable.  

As for system resources, I've got a 4Ghz quad core CPU and 32GB of RAM...so I should be fine.  I'm running a GTX 1060 video card (6GB) -- will Ubuntu be able to utilize that card?  

Sorry for all the noobie questions, but I have to be certain this stuff will work.  Like I said, the Adobe suite is critical, and I'd really like Skyrim to work as well.  

I just wish I could find a way to test all this without wiping out my current set up.  Can I run a VM inside a VM (Windows inside Ubuntu, inside Windows) and get accurate results?

---

### Post by dragonfly41 on 2017-04-13
Why not experiment first with a live Ubuntu USB or better Ubuntu installed in an external USB drive container?
You don't need to touch your Windows setup.
Ubuntu might run a bit slower via USB but you can test functionality of apps.
On the other hand you have plenty of RAM.
There is a windows utility UNetBootin which can take a Ubuntu download iso and create USB.

---

### Post by Perfect Storm on 2017-04-13
If you use the steam version of Skyrim it gets gold rating with the application Wine: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=13667](https://appdb.winehq.org/objectManager.php?sClass=application&iId=13667) But don't expect the same performance as in Windows.

---

### Post by Bucky Ball on 2017-04-13
> **thepentool said:**
> I'm running a GTX 1060 video card (6GB) -- will Ubuntu be able to utilize that card?

That card will work fine. In fact, if you look in 'Additional Drivers' once you've updated and installed you will find the NVidia driver there for it (you need the Canonical Partner repositories enabled for this, but we can help you with that when you get there; easy to do).

Gaming in a VM is a pointless exercise, which is my only concern with some of your graphics stuff. Wouldn't dream of video or audio production in a VM.

---

### Post by thepentool on 2017-04-13
> **dragonfly41 said:**
> Why not experiment first with a live Ubuntu USB or better Ubuntu installed in an external USB drive container?
You don't need to touch your Windows setup.
Ubuntu might run a bit slower via USB but you can test functionality of apps.
On the other hand you have plenty of RAM.
There is a windows utility UNetBootin which can take a Ubuntu download iso and create USB.

I have a 64GB USB 3.0 Flash Drive...what would I need to do to install Ubuntu onto it?  And that's not a LiveCD type thing, right?  It's an actual install?

> **Artificial Intelligence said:**
> If you use the steam version of Skyrim it gets gold rating with the application Wine: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=13667](https://appdb.winehq.org/objectManager.php?sClass=application&iId=13667) But don't expect the same performance as in Windows.

I've used Wine in the past, and it's been a hit-and-miss type of thing.  Why shouldn't I expect the same performance, though?  

> **Bucky Ball said:**
> That card will work fine. In fact, if you look in 'Additional Drivers' once you've updated and installed you will find the NVidia driver there for it (you need the Canonical Partner repositories enabled for this, but we can help you with that when you get there; easy to do).

Gaming in a VM is a pointless exercise, which is my only concern with some of your graphics stuff. Wouldn't dream of video or audio production in a VM.

Why is gaming in a VM pointless?  Isn't that the whole idea of VMs, that you can run Windows programs without running Windows natively?  Not trying to be argumentative, I'm just honestly curious.  :)

---

### Post by dragonfly41 on 2017-04-13
> [COLOR=#000000]I have a 64GB USB 3.0 Flash Drive...what would I need to do to install Ubuntu onto it? And that's not a LiveCD type thing, right? It's an actual install?[/COLOR]
It is some time since I've created a Live USB from Windows.

I have previously used **UNetBootin** but this article suggests using **Rufus** in Windows (I have not used this).

[https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](https://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

Now if you intend to use the USB version of Ubuntu it is important to set it up as **persistent**.   Otherwise any files you create will disappear when you reboot.

This article explains how to use **mkusb** from within Ubuntu to make a persistent live USB.

[https://askubuntu.com/questions/772744/how-to-make-a-live-usb-persistent](https://askubuntu.com/questions/772744/how-to-make-a-live-usb-persistent)

You will need to research which installer Windows allows creation of a persistent Live USB.


The process I use .. in fact quite recently .. is to create a Live USB from within Ubuntu (not Windows) and then use that to install in an external USB drive where partitions are created using Gparted (in Ubuntu).

I would not do any partition management from Windows since it does not make it easy.
[B]
BUT[/B] .. before taking this approach I realise there is another option you could consider.

You can install VirtualBox on Windows and then install Ubuntu as a virtual machine in Windows Virtual Box.

You could then install graphics tools in Ubuntu VM and experiment .. while running Windows.

---

### Post by wildmanne39 on 2017-04-13
Rufus is very easy to use and works great in windows.

If I remember correctly is does not create a short cut, you have to go into the Rufus folder to run it.

---

### Post by thepentool on 2017-04-13
I'd really like to try these things with Ubuntu running as the base layer.  I'll look into installing Ubuntu to a USB device and see if I can get that up and running.  That will let me test everything without wiping my main drives, and if all goes well, maybe I can install a VM into that Ubuntu install and load Windows 10.  

Do all these tips apply to all versions of Linux (like, elementaryOS?), or just Ubuntu?

Thanks again for the help guys.  Seems like a lot of work to get started, but it would be worth it, I think, if I can get everything going the way I need it to.

---

### Post by dragonfly41 on 2017-04-13
This is a postscript.

Some extra discussion here .. [https://www.groovypost.com/howto/really-run-linux-from-a-memory-card/](https://www.groovypost.com/howto/really-run-linux-from-a-memory-card/)
explaining that after you create your persistent live USB and attempt to boot it up ..
remember during installation of USB  to have added **boot flag** to the root partition in USB (to ensure it is bootable)
and when you boot up you will first need to go to your **PC BIOS** to select and prioritise
"boot from USB" instead of default for Windows "boot from internal HDD".

> [COLOR=#000000]Do all these tips apply to all versions of Linux (like, elementaryOS?), or just Ubuntu?
[/COLOR]I can only confirm that UNetBootin provides a drop down menu for you to choose the distro (not only Ubuntu).
I don't know if Rufus provides a choice of distros.

Good luck.

---

### Post by ka55o5 on 2017-04-13
****> **thepentool said:**
> Last time I used something like VirtualBox, there was no 3D support for video [..]
There is *very limited* 3D support which can be installed with the Oracle VM VBoxGuestAdditions - when booting the VirtualBox VM in **Safe Mode** && it's marked as "Experimental", unfortunately.

Search queries:```
1) https://www.google.com/search?q=Oracle+VM+VBox+Guest+Additions+safe+mode+3d+support
2) https://duckduckgo.com/?q=Oracle+VM+VBox+Guest+Additions+safe+mode+3d+support
3) https://www.startpage.com/rvd/search?query=Oracle+VM+VBox+Guest+Additions+safe+mode+3d+support
```
This is the basic page of their manual:```
https://www.virtualbox.org/manual/ch04.html
```> **Note**
For the basic Direct3D acceleration to work in a Windows Guest, you have to install the Guest Additions in "Safe Mode". This does not apply to the experimental WDDM Direct3D video driver available for Vista and Windows 7 guests, see Chapter 14, Known limitations for details.[18]

Besides some of the more outlandish (hehe) suggestions in this thread... What I do (& it sucks!..:)) is dual boot Window$ with *nix, because there's not other way. Idk., WINE *might support some versions* of Adobe, but who knows how well - at the end of the day (which, sometimes, may **not** even be such a bad thing, being able to avoid some of Adobe's "features" - for example, **the endless drivers** which it will want to insert into the Window$ boot, heh.)

However, I had it set up beforehand... NOT using a GPT disk, but instead *regular* partitions: there are maximum of four (4) Primary partitions supported by the MBR (NTFS) && after creating two (2) for my Window$ and its data, I left a BLANK, **unpartitioned**, space at the end of the drive - so that the Ubuntu installer would recognize the situation and present its GUI option to install alongside of Windows; it, then, creates all of the needed Linux partitions there.

[EFI boot and GUID]("https://superuser.com/questions/370016/why-can-i-only-have-four-partitions") partition tables is something that I purposefully avoid, ESPECIALLY when installing Windows 10. I *really* don't want any of their "Secure Boot" and other madness to dictate what goes on. Btw., **also**, when installing Window$, it's not a terrible idea to start it by manually creating the partitions: for example, in the case of Windows 7, the setup installer will create two (2) partitions and you can remove the "100MB System Reserved" partition - in order to have Window$ reside on just one Primary partition (although there are [possible drawbacks]("https://www.google.com/search?q=windows+7+setup+remove+system+reserved+partition") (just in extreme cases, maybe BitLocker won't work as it'll have nowhere to store the keys), it can also be considered as hardening the system because some automated scripts can be avoided in this way). 

... Couldn't quick-search a nice page for this, but here are two links - nevertheless:```
1) https://zedstips.blogspot.com/2012/04/trick-to-remove-10000-mb-system.html
2) https://jagatsheth.wordpress.com/2010/01/25/remove-100mb-system-reserved-partition-installing-windows-7/
```
[color=gray]The second example deleted the System Reserved partition, while in fact the second partition can be deleted and then the first one simply extended; it **will** end up as active, primary, boot and with all the right flags.[/color]

Whoa, ok... I REALLY hadn't meant to write this wall-of-text, but I sincerely hope that at least some of the info here will be useful! :) :)

P.S. 
Ah, gawd (!), ofc., I have to add even more, blah... As the GRUB 2 bootloader is installed to run this kind of a dual-boot setup, when something goes wrong with Window$, you gotta boot from its install media and: **1**) /fixmbr and **2**) /fixboot and after repairing that... It's onto restoring GRUB 2 to get all the boot options back. xD 

```
https://neosmart.net/wiki/fix-mbr/
```[color=gray]Hope it helps![/color]

**Edit**: Forgot to add, while VMware *may*, possibly, have some "better" features, installing it **will** create a WHOLE MESS - so, just, btw., also [s]perhaps[/s] something to consider. =)```
https://technet.microsoft.com/en-us/sysinternals/bb963902.aspx
```
^^ Microsoft Autoruns for Windows (Windows Sysinternals) is a great tool to record the pre-install boot-driver situation && then compare afterwards (when the OS gets loaded with the Adobe and/or VMware drivers).

---

### Post by ka55o5 on 2017-04-13
> **wildmanne39 said:**
> Rufus is very easy to use and works great in windows.
> **dragonfly41 said:**
> I can only confirm that UNetBootin provides a drop down menu for you to choose the distro (not only Ubuntu).
I don't know if Rufus provides a choice of distros.
No, I don't think it does **and**, also, they use different methods of packing /unpacking the Window$ data onto the install media - so, IMO, UNetbootin is the way to go (just saying. :))

---


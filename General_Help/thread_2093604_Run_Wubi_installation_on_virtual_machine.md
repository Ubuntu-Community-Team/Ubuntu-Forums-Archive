---
title: "Run Wubi installation on virtual machine"
date: 2012-12-11
forum: General Help
---

### Post by aHcVolle on 2012-12-11
Hi,

i'm searching for a way to boot my ubuntu installation (installed with wubi) in any kind of virtual machine.
Back in 2009 [mbeichorn]("http://ubuntuforums.org/member.php?u=855957") asked the same question in [this thread]("http://ubuntuforums.org/showthread.php?t=1232698") and [horse_dung]("http://ubuntuforums.org/member.php?u=1060361") provided the useres with some kind of virtualbox vm that was capable of booting WUBI Ubuntu 10.04 LTS on a Win7 host machine.

Unfortunately the scripts aren't accessible anymore and i can't download them. I don't know if they would be a help at all because they were for Ubuntu 10.04 but they would be  a good start for this. 

What horse_dung basically did was he mounted the wubi root.disk in a virtual machine where grub was installed. Grub then mounted the wubi disk as loop device and booted the ubuntu installation.

Another approach is to use [vboot provided by vmlite]("http://www.vmlite.com/index.php?option=com_content&view=article&id=51&Itemid=148") but this isn't availiable for Ubuntu 12.10.

Both ways are way over my knowledge of linux at all, so i would need some kind of tutorial or point to start to learn such things.

So back to my question. Is there any way (it really doesn't matter to me which way) to have a Ubuntu 12.10 64bit installation running like a natively installed version of Ubuntu and additionally as VM on my Win8 64bit Machine.

One way that i can think of is that i could install Ubuntu without Wubi and then boot my Ubuntu Partition with virtualbox's raw partition access. But that would mean that i'd have to mess around with my win8 bootloader and grub, both thinks i really don't want to touch.

To be clear, i don't care about the VM Software. If it's Virtualbox, qemu, VMWare or any other VM Software is completely open, but Virtualbox would be my first choise.

Thanks in advance
 Chris

---

### Post by Ms. Daisy on 2012-12-11
> Is there any way (it really doesn't matter to me which way) to have a  Ubuntu 12.10 64bit installation running like a natively installed  version of Ubuntu and additionally as VM on my Win8 64bit Machine To accomplish that, I would recommend that you dual boot windows and ubuntu- that would install both on your hardware. This is the only option that would truly allow both windows and windows to run "like a natively installed version."

But you can accomplish a similar outcome in a variety of other ways:

- install virtualbox/vmware/whatever on Windows and install ubuntu in a virtual machine.
- install virtualbox/vmware/whatever on Ubuntu and install Windows in a virtual machine.
- Install wubi (which would give you Ubuntu) inside of a Windows installation.

I suppose you could try to install wubi inside of a windows virtual machine, but I would imagine that would be highly resource-intensive and probably wouldn't run very efficiently unless you've got a really powerful computer.

---

### Post by aHcVolle on 2012-12-12
Hey,

thanks for your reply but this isn't what i'm trying to do.
Booting windows and Ubuntu side by side isn't hard, the problems start when i'm trying to boot the installed linux in a VM too.

Chris

---

### Post by Mark Phelps on 2012-12-12
Wubi already installs using a "virtual" file system.  The whole purpose is to prevent you from having to deal with partitioning to install Ubuntu.

Since you are using a VM already, embedding Wubi inside that is NOT going to have it run like a native version.

Why not just install Ubuntu in the VM, instead of messing around with Wubi?

---

### Post by JKyleOKC on 2012-12-12
> **aHcVolle said:**
> Hey,

thanks for your reply but this isn't what i'm trying to do.
Booting windows and Ubuntu side by side isn't hard, the problems start when i'm trying to boot the installed linux in a VM too.

ChrisCan you be a bit more clear as to why you want "to boot the installed linux in a VM too"? Having two instances of a single copy of the system could be akin to juggling bottles of nitroglycerine, since actions on one instance would not necessarily be duplicated instantly in the other. That's why the virtualbox on-line manual warns so intensely about the dangers of mounting a physical system as a virtual machine.

You can do all sorts of things in virtualbox using its command-line interface, VBoxManage. For instance, I have a launcher in my xubuntu panel that can select from half a dozen VMs I've defined, and once selected that VM either boots itself or restores itself from "saved" state with no additional action on my part. If that's what you want, it only takes one call to accomplish: "VBoxManage startvm books" launches the VM named "books".

If you tell us more about your goal, perhaps we can help you more...

---

### Post by aHcVolle on 2012-12-13
> **Mark Phelps said:**
> 
Why not just install Ubuntu in the VM, instead of messing around with Wubi?

You are right but the wubi installation would have complete hardware access while the VM Vesion doesn't.

> **JKyleOKC said:**
> Can you be a bit more clear as to why you want "to boot the installed linux in a VM too"? Having two instances of a single copy of the system could be akin to juggling bottles of nitroglycerine, since actions on one instance would not necessarily be duplicated instantly in the other. That's why the virtualbox on-line manual warns so intensely about the dangers of mounting a physical system as a virtual machine.

You can do all sorts of things in virtualbox using its command-line interface, VBoxManage. For instance, I have a launcher in my xubuntu panel that can select from half a dozen VMs I've defined, and once selected that VM either boots itself or restores itself from "saved" state with no additional action on my part. If that's what you want, it only takes one call to accomplish: "VBoxManage startvm books" launches the VM named "books".

If you tell us more about your goal, perhaps we can help you more...

I don't want to boot both Ubuntu versions at the same time.

My Goal of this whole mess is that i want to switch from windows to ubuntu slowly. Since Valve's Ubuntu Version of Steam is currently in Beta gaming on a Linux machine will be much easier in a few months i think. 

Since i've got a Tripple monitor Setup on my machine i can easily use one of these screens for displaying a Ubuntu VM while working on my Windows machine. 
But using a VM won't allow me to play games due tu the lack of direct Hardware access. I'd like to "work" on my windows machine, play around (learn using Linux) with ubuntu in a VM and when i want to play games or more hardware demanding applications start ubuntu natively without a vm.

---

### Post by JKyleOKC on 2012-12-13
I'm not a gamer so have no direct knowledge, but from messages in the forums over the years I suspect that the wubi installation will have too much latency to meet your expectations for use in the games, since the additional latency is noticeable to many users even in non-game use. You might be better off to do a side-by-side dual-boot setup, then use the methods outlined in the vbox manual and forum how-tos to run the Ubuntu side in a VM also.

Also, virtualbox now has 3D video emulation although it's still noted as "experimental" so I've not tried it. This might overcome the direct-access-to-hardware problem, although the increased latency would definitely be a handicap in games.

---

### Post by Mark Phelps on 2012-12-13
> **aHcVolle said:**
> You are right but the wubi installation would have complete hardware access while the VM Vesion doesn't.


OK ... but I thought you said originally you wanted to run Wubi INSIDE a VM -- so why wouldn't it then suffer from the same hardware access limitations as running anything else in the VM?

---

### Post by aHcVolle on 2012-12-17
> **JKyleOKC said:**
> ... I suspect that the wubi installation will have too much latency to meet your expectations for use in the games, since the additional latency is noticeable to many users even in non-game use. ..

Also, virtualbox now has 3D video emulation although it's still noted as "experimental" so I've not tried it. This might overcome the direct-access-to-hardware problem, although the increased latency would definitely be a handicap in games.

I think the only additional latency comes from file access or am i wrong (i didn't compare but this is the only thing i can think of), which wouldn't bother me much because it would only be noticable on e.g. map loading of a game..

You are right, Virtual box has 3D emulation but as you said this addidtional latency would make a game unusable i think. I haven't tried it but i don't think i could use all my gaming power in a VM.

> **Mark Phelps said:**
> OK ... but I thought you said originally you wanted to run Wubi INSIDE a VM -- so why wouldn't it then suffer from the same hardware access limitations as running anything else in the VM?

no i dont want to run wubi in a VM, i want to run the ubuntu installation installed by wubi in a VM. I'm sorry if i didn't say that clear.

- Chris

---

### Post by Mark Phelps on 2012-12-17
> **aHcVolle said:**
> no i dont want to run wubi in a VM, i want to run the ubuntu installation installed by wubi in a VM. I'm sorry if i didn't say that clear.

OK ... then it looks like you want to "migrate" an existing Ubuntu installation, using a root.disk file inside a Windows partition, into a VM, right?

Sorry, can't advise you there because I haven't personally used VM in a long time, and last time I did, you had to INSTALL the OS to the VM, you couldn't simply copy files there and have it work.

But once again, even if you COULD migrate the Wubi-install to a VM, wouldn't THAT still suffer from the same limitations as an install?

---

### Post by oldfred on 2012-12-17
I do not think you are going to get what you want, but I have this old thread from meierfra who did bootinfoscript. I think he just wanted to show it could be done.


       See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

I also have this in my notes, but know nothing about VM's.

       wubi direct boot
menuentry "Wubi" {

 insmod ntfs
set root=(hd0,2)

         loopback loop0 /ubuntu/disks/root.disk
 set root=(loop0)
linux /vmlinuz root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
initrd /initrd.img

 }

---

### Post by aHcVolle on 2012-12-17
> **Mark Phelps said:**
> OK ... then it looks like you want to "migrate" an existing Ubuntu installation, using a root.disk file inside a Windows partition, into a VM, right?
But once again, even if you COULD migrate the Wubi-install to a VM, wouldn't THAT still suffer from the same limitations as an install?

Yes, i think now you know what i mean. You are right, when i'm using the wubi installation in the VM i'd have all the limitations of the vm but i could boot the installation "natively" using wubi to have the complete hardware power (minus the little harddisk overhead that every wubi installation has got)

> **oldfred said:**
> I do not think you are going to get what you want, but I have this old thread from meierfra who did bootinfoscript. I think he just wanted to show it could be done.
...


While this looks very promising and is in fact half of the job. It will help me as soon as i get the root.disk file recognized inside the VM.
Now the only task is to get this file somehow linked to the VM (not copied!!).

But as i'm writing this i think i should head over to the virtualbox's Forum and see if i can get help over there.

- Chris

---

### Post by JKyleOKC on 2012-12-17
Chris,

One of the problems I uncovered when I researched the whole idea of running an existing physical installation inside a VM was that the hardware used by the physical installation is almost always significantly different from the "virtual hardware" that the VM provides -- and this requires that the drivers be changed in order for the system to run inside the VM.

With Windows and its separate drivers, this can be accomplished by creating a second hardware configuration in the system administration menus; at least, it could for WinXP which is what I was researching. It was necessary to do so, and then make sure that one never tried to have both configurations running at the same time, even momentarily. That requirement is what convinced me to abandon the whole idea.

For Linux, where the drivers are integrated into the kernel and to some degree permanently configured at install time, I'm not even sure that such dual hardware setups are possible. They may well be, but I'm sure it's not as simple as it may seem at first glance. Just one more thing to consider and do your research on...

---

### Post by aHcVolle on 2012-12-18
> **JKyleOKC said:**
> ...
For Linux, where the drivers are integrated into the kernel and to some degree permanently configured at install time, I'm not even sure that such dual hardware setups are possible. They may well be, but I'm sure it's not as simple as it may seem at first glance. Just one more thing to consider and do your research on...


OK that might be a problem. To be honest i thought that this was only a problem in the "windows world". I thought that linux could handle HW changes much better that windows. I'll try that with a "normal" installed linux booting in a VM, what seems to be no big problem (data wise). If this works flawless (which i don't think after your post) then i'll jump back to this problem here.

- Chris

---

### Post by Cheesemill on 2012-12-18
> **JKyleOKC said:**
> For Linux, where the drivers are integrated into the kernel and to some degree permanently configured at install time, I'm not even sure that such dual hardware setups are possible. They may well be, but I'm sure it's not as simple as it may seem at first glance. Just one more thing to consider and do your research on...

Linux is much more forgiving of hardware changes than Windows. The drivers aren't configured at install time, the kernel probes for available hardware and loads the correct drivers *every time you boot*.

This is why you can just pull a hard drive from one machine and boot from it in another with no issues.

The only time you will get problems is if you have installed any restricted drivers. This will stop you booting if the drive is switched from a machine with Nvidia graphics to one with ATI graphics for example. If you don't install the restricted drivers this won't be a problem.

---

### Post by aHcVolle on 2012-12-18
> **Cheesemill said:**
> Linux is much more forgiving of hardware changes than Windows.

Thats how i thought it is. Thanks for clearing that up.

 -Chris

---


---
title: "Live CD freezes, need reinstall GRUB, desperate!"
date: 2007-11-24
forum: General Help
---

### Post by PeterMo on 2007-11-24
Well as the subject says I need to reinstall GRUB bootloader on my MBR. And I'm desperate.
Also, I have to prepare the presentation of my Masters thesis which is on Thursday and all my stuff is on the linux partition. So I'm kind of in a hurry.

The PROBLEM I have is that something in my hardware setup is broken so I can't use my nvidia drivers in Windows. It will freeze the system on starting windows desktop. (I tried a LOT of solutions/combos so let's just say I've given up, also it's off-topic). I can only run windows using the default VGA-driver and it's horribly slow, but it works. HOWEVER:
I DID manage to boot into Ubuntu for some reason. It froze on me once when initializing Gnome but I rebooted and tried again and it worked. One of the things I tried was to locate my problem was to reinstall Windows, and as we all know it wipes the MBR and GRUB. So I downloaded the Ubuntu Live CD and tried to boot from it, BUT, the Live CD freezes, just like Windows does when initializing the desktop. Safe mode did the same thing (What's safe about it anyway?)
I've tried the Alternate Install CD but only found a lot of install-options. I don't want to install! I've also tried "Ultimate Boot CD", but I can't get any of those linux boot disks on it to do what I want. Either chroot and mount is missing or for some reason my drive with the linux partitions on doesn't appear and god knows what.

My question is:
Is there a way to just boot Ubuntu from the Live CD WITHOUT starting any graphical environment?

I've read that you can make a simple boot CD from inside Ubuntu with kernel and some basic stuff on it, and that's pretty much what I need. Something to boot from so I can chroot to my linux partition and run the grub installer again. Can I get such a CD from somewhere? I've seen millions of CDs everywhere with different distros and boot-CDs and all kind of stuff and frankly I'm running out of CDs to burn.

So. Can I start the Live CD WITHOUT X or does anybody have a bootable text-only CD I can burn?

Please :(

/Peter

---

### Post by -grubby on 2007-11-24
you can't boot into a non-graphical environment with the live-cd. Try the alternative c

---

### Post by PeterMo on 2007-11-24
Hi, thanks for your reply.
Can I actully get a console by using the Alternative CD? It only presents me with a lot of installation options. I don't really want to overwrite what I have on my linux partition so I'm afraid of using any of the installation choices. Could you give me a quick hint on what I need to do please?
All I need is to access my existing linux partition and run the grub installer from it.

---

### Post by markk1994 on 2007-11-24
Get the Super Grub boot disk and reinstall grub from there 
its a pretty small file about 3 mb last time i checked Burn it as a boot disk
and boot and find the option to reinstall Grub and your on your way to getting your computer back to normal :)

---

### Post by PeterMo on 2007-11-24
> **markk1994 said:**
> Get the Super Grub boot disk and reinstall grub from there 
its a pretty small file about 3 mb last time i checked Burn it as a boot disk
and boot and find the option to reinstall Grub and your on your way to getting your computer back to normal :)

Thanks!
I will try it right away!

---

### Post by PeterMo on 2007-11-24
> **markk1994 said:**
> Get the Super Grub boot disk and reinstall grub from there 
its a pretty small file about 3 mb last time i checked Burn it as a boot disk
and boot and find the option to reinstall Grub and your on your way to getting your computer back to normal :)

[SIZE="3"]It worked!!![/SIZE]

[SIZE="7"]YOU'RE THE MAN!!![/SIZE] :guitar:

A thousand thanks!!!! I was going insane here!
Oh that feels so relaxing! Now I can return to feeling the ordinary stress of getting my report done! :)
THANK YOU!!

---


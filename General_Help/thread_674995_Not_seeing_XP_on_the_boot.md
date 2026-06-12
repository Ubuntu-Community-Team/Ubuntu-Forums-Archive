---
title: "Not seeing XP on the boot"
date: 2008-01-22
forum: General Help
---

### Post by whatsupbraaahh on 2008-01-22
Hey everybody,
I'm new to Ubuntu, and decided to install based on what I saw on the livecd. Anyways, after I installed, I updated my Ubuntu software, and restarted my computer. I decided to go to the bootloader to boot into XP, which I had before, since I wanted to transfer all my school e-mail on Outlook over to Evolution e-mail. The bootloader showed the Ubuntu OS but didn't show any other operating systems. I made sure to do the partition when installing, and saw when it was installing the creation of the partition and the search for the other OSs. Any help to be able to get XP onto that bootloader would be fantastic.

Thanks!

---

### Post by stoneybroke on 2008-01-22
Did you install windows first or Ubuntu?

---

### Post by djrobthaman on 2008-01-22
@ stoneybroke: The fact that ubuntu loads means that ubuntu was installed after windows, otherwise windows would have overwritten the mbr and the problem would be reversed (windows would load with no option to boot ubuntu)

@ the OP: If you open gnome partition editor (if you don't have it look for it in add/remove programs and install it) do you see the partition with windows on it?  If you do I believe it's a simple edit of the grub loader settings.  I think (am not 100% sure) that all you need to do is open up /boot/grub/menu.lst and either insert the following lines or edit what is there to make it look like the following

```

title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

```

---

### Post by sandysandy on 2008-01-22
> **whatsupbraaahh said:**
> Hey everybody,
I'm new to Ubuntu, and decided to install based on what I saw on the livecd. Anyways, after I installed, I updated my Ubuntu software, and restarted my computer. I decided to go to the bootloader to boot into XP, which I had before, since I wanted to transfer all my school e-mail on Outlook over to Evolution e-mail. The bootloader showed the Ubuntu OS but didn't show any other operating systems. I made sure to do the partition when installing, and saw when it was installing the creation of the partition and the search for the other OSs. Any help to be able to get XP onto that bootloader would be fantastic.

Thanks!

Open terminal (using the following path Applications ---> accessories ----> terminal)

post output of code [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by whatsupbraaahh on 2008-01-22
djrobthaman- checked it out, looked pretty much the same as the code you posted except it said Windows 2000/XP or something along those lines for the name.


sandysandy- heres what it said:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x842a842a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114190019    57094978+  83  Linux
/dev/sda2       114190020   117210239     1510110    5  Extended
/dev/sda5       114190083   117210239     1510078+  82  Linux swap / Solaris

---

### Post by djrobthaman on 2008-01-22
Why don't you try installing startupmanager using synaptic (just saw something about it online).  It's supposed to be a gui for editing the grub bootloader preferences.  If this works as well as some people say it does, then it should help out your situation.

---

### Post by ugm6hr on 2008-01-22
> **whatsupbraaahh said:**
> sandysandy- heres what it said:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x842a842a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   114190019    57094978+  83  Linux
/dev/sda2       114190020   117210239     1510110    5  Extended
/dev/sda5       114190083   117210239     1510078+  82  Linux swap / Solaris

Errrmmm...

There is no XP partition there.

This tells me you have a 60GB HD with 2 partitions (sda1=Ubuntu & sda5=swap).

Are you sure you didn't use the "Guided" install option and tell it to use the whole HD?

Whatever you did, it appears you wiped XP.

---

### Post by whatsupbraaahh on 2008-01-22
hmm.... if that's so then that sucks. I don't have the windows cd since the computer I use is the one my school gave me. I might just have to backup the stuff I still have on the drive to my external, then reinstall windows I guess. maybe, I'll just dual-boot with macosx from one of the osx projects. thanks alot guys.

---

### Post by whatsupbraaahh on 2008-01-22
also... I checked out the startup-manager (which was actually pretty helpful, although it does seem like I wipe XP off). But since all my outlook settings were on XP, any ideas on how to get them at all, or did that go with XP?

---

### Post by djrobthaman on 2008-01-22
If you deleted the xp partition then, yes, it did go with xp.  But there are programs you can use to try and get it back.  I don't know of any ubuntu programs (maybe someone else can fill you in on that) but if you reinstall windows I remember when something similar happened to me a couple years back I used something that was called RecoverMyFiles (or something close).

So all hope is not lost.

---

### Post by ugm6hr on 2008-01-22
> **whatsupbraaahh said:**
> hmm.... if that's so then that sucks. I don't have the windows cd since the computer I use is the one my school gave me. I might just have to backup the stuff I still have on the drive to my external, then reinstall windows I guess. maybe, I'll just dual-boot with macosx from one of the osx projects. thanks alot guys.

Since you have installed Ubuntu *over* XP, I suspect that you have wiped absolutely everything from the XP partition.  I can't see any point in backing up a newly installed Ubuntu installation.

Dual-boot OSX?  Not strictly legit....

And if you don't have an XP disc / license - reinstalling is going to be a bit tricky...

Maybe your school IT guy can reinstall XP for you (if you wipe the drive completely with something like active killdisk and claim ignorance ;)

PS: Dual-boot with Ubuntu is easily done, as long as you follow correct instructions!

---

### Post by whatsupbraaahh on 2008-01-22
haha... yea, it definitely was, but that's what I get for trying to install a new os at 4 in the morning after being up all day, just a bit tired haha

---


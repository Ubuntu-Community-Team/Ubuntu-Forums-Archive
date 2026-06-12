---
title: "Chain-load w two hard drives"
date: 2008-06-28
forum: General Help
---

### Post by weedwacker on 2008-06-28
I want to be able boot to either Windows XP Pro or Ubuntu Hardy via the GRUB menu.

My setup is Windows is on my first SATA drive and Ubuntu is on my second SATA drive.

When Ubuntu was installed I disconnected my Windows hard drive so that my Windows MBR would not be affected by the Ubuntu install.

Currently, when I want to boot into either Windows or Ubuntu, I have to enter my BIOS and change the choice of booting into the first drive or the second.

I would like to be able to boot up my computer and be given a choice of either Windows or Ubuntu, much like the menu you get if you setup a dual boot on the same hard drive.

I have read the threads that discuss chain loading, but either I don't understand them, or they discuss situations where Windows is set up on the _second_ hard drive, not the first.

Thanks in advance.

---

### Post by cariboo on 2008-06-28
I would advise reinstalling grub with both hard drives connected, It will save a lot of problems.

Jim

---

### Post by danwood76 on 2008-06-28
With regards to chainloading its very simple, you add an extra entry to the menu.lst something like this:

```

title Windows
root (hd0,0)
chainloader +1

```
That then chainoads the OS stored on that partition.
As already stated you should let grub install itself on the MBR  otherwise you will have lots of issues getting grub setup properly.
You can always reinstall the windows MBR very easily from ubuntu or from the live CD.

---

### Post by logos34 on 2008-06-28
Actually, you need ['mapping']("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") in the windows stanza since vista is on second hard disk:

> title        Windows Vista
root        (hd**1**,0)
savedefault
makeactive
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
chainloader    +1

(*or maybe windows is the second partition, in which case ' root (hd1,1)'--grub starts counting from 0)

---

### Post by weedwacker on 2008-06-28
> **danwood76 said:**
> With regards to chainloading its very simple, you add an extra entry to the menu.lst something like this:

```

title Windows
root (hd0,0)
chainloader +1

```
That then chainoads the OS stored on that partition.
As already stated you should let grub install itself on the MBR  otherwise you will have lots of issues getting grub setup properly.
You can always reinstall the windows MBR very easily from ubuntu or from the live CD.

Thanks, Danwood76--

This is the info that I wanted.  I am concerned, however, that I may have lots of issues getting GRUB set up properly if I use the chainload method.  You said that I could always reinstall the windows MBR from Ubuntu or the live CD if necessary.  Hmmm.  I think I need to find out how to do that.

However, thanks for your quick response!

---

### Post by logos34 on 2008-06-28
weedwacker,

You won't be able to use grub to chainload vista on the other drive without mapping (basically to trick windows into thinking it's the Bios boot drive)...Unless you want to overwrite the vista bootloader with grub and boot from that drive instead

---

### Post by weedwacker on 2008-06-28
> **logos34 said:**
> weedwacker,

You won't be able to use grub to chainload vista on the other drive without mapping (basically to trick windows into thinking it's the Bios boot drive)...Unless you want to overwrite the vista bootloader with grub and boot from that drive instead

Hey, Logos34...

Thanks for the comment.

I thought mapping was used when Ubuntu was installed on the first hard drive and windows was installed on the second hard drive.???

My concern is that the first time I installed Ubuntu it was a dual boot with Windows on the same hard drive.  Of course I screwed up a few times as I was learning Ubuntu.  Somewhere along the way I lost Ubuntu and Windows so I had to go through the whole nine yards with a fresh install of Windows XP Pro 64bit (I think this version of Windows with its awkward install system - install on AMD and ASUS board and having to load VIA drivers by means of a floppy - what a pain!) was a bit much.  And then I had to reinstall Ubuntu as a dual boot again.  Sometime later I had to go through the process again!!

Anyway, this put me off dual booting on a single hard drive and so I got a second drive exclusively for Ubuntu.  This works for me as long as I don't mind booting into my BIOS and changing the hard drive load up priority whenever I want to boot to the other OS.

But this idea of chain loading intrigued me so I am investigating.

But now, since I have done a fresh installation of Hardy, I think I'll sit on this for a while and mull it over.

Anywho, thanks for your comments

---

### Post by logos34 on 2008-06-28
> **weedwacker said:**
> I thought mapping was used when Ubuntu was installed on the first hard drive and windows was installed on the second hard drive.???

(you're correct about windows--actually it's more correct to say 'non-first hard disk').  Ubuntu can be installed anywhere (first disk, second disk, etc.)...what matters is what disk/mbr Grub (specifically, stage1) is on.  If you want to keep your windows bootloader on the first sata

> When Ubuntu was installed I disconnected my Windows hard drive so that my Windows MBR would not be affected by the Ubuntu install.

then you'll need to install grub to the second sata (ubuntu drive).  But since you will then be booting to Grub on the ubuntu drive, XP will be second in the Bios hard disk boot order.  Since windows refuses to boot unless it thinks it is the Bios boot drive, you'll have to use the map lines trick to fool it.

>  Anyway, this put me off dual booting on a single hard drive and so I got a second drive exclusively for Ubuntu.  This works for me as long as I don't mind booting into my BIOS and changing the hard drive load up priority whenever I want to boot to the other OS.

But this idea of chain loading intrigued me so I am investigating.


I understand your concerns.  You can certainly just toggle the boot drive in the bios each time.  Or chainload it with grub, but you need the mapping.

enjoy

---

### Post by weedwacker on 2008-06-29
> **logos34 said:**
> (you're correct about windows--actually it's more correct to say 'non-first hard disk').  Ubuntu can be installed anywhere (first disk, second disk, etc.)...what matters is what disk/mbr Grub (specifically, stage1) is on.  If you want to keep your windows bootloader on the first sata



then you'll need to install grub to the second sata (ubuntu drive).  But since you will then be booting to Grub on the ubuntu drive, XP will be second in the Bios hard disk boot order.  Since windows refuses to boot unless it thinks it is the Bios boot drive, you'll have to use the map lines trick to fool it.



I understand your concerns.  You can certainly just toggle the boot drive in the bios each time.  Or chainload it with grub, but you need the mapping.

enjoy

Thanks, Logos34,

Your explanation is really helpful.  This is all beginning to make sense to me.  I'm going to take a shot at doing it your way. First, I'll back up data and make an off-computer copy of instructions for editing my boot grub menu.lst should I need to recover the grub.

Wish me luck!! :):)

---

### Post by weedwacker on 2008-07-02
OK, let's do a recap here.

[COLOR="Red"]First[/COLOR], I perhaps should have said that both of my hard drives are sata; one a Maxtor with Windows installed and the second a Seagate with Ubuntu installed. Ubuntu was installed with the Windows hard drive disconnected so the GRUB would not overwrite the Windows MBR.

When I do a [COLOR="Blue"]find /boot/grub/stage1[/COLOR] the response is: [COLOR="Blue"](hd1,0)[/COLOR]

[COLOR="Red"]Secondly[/COLOR], the boot order in my BIOS is:
[INDENT]1st boot: 2nd hard drive (Ubuntu)
2nd boot: 1st hard drive (Windows)[/INDENT]

[COLOR="Red"]Thirdly[/COLOR], per helpful direction from forum members and other sources, this is what my menu.lst looks like:
-----------------------------------------
## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0f70645e-876f-4c24-bf54-7228b88d91a2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0f70645e-876f-4c24-bf54-7228b88d91a2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0f70645e-876f-4c24-bf54-7228b88d91a2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0f70645e-876f-4c24-bf54-7228b88d91a2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Title      Windows XP Professional 64
rootnoverify  (hd1,0)
savedefault
makeactive
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader   +1
-----------------------------------

When I boot up my GRUB screen has no entry for Windows. I think I did the correct thing by placing the chainloader mapping entry [COLOR="Red"]*after*[/COLOR] the "### END DEBIAN AUTOMAGIC KERNELS LIST".

Any suggestions as to why a Windows option does not appear on my GRUB boot up screen?  I have a 10 second delay to view that screen.

---

### Post by danwood76 on 2008-07-02
Well it looks like it should be fine.
All your mappings etc look correct and partition numbers etc.

Are you sure you've scrolled all the way to the bottom of the list?
A guy in another thread hadn't done so, but you dont really have enough entries for that to be the case.

The '### END DEBIAN AUTOMAGIC KERNELS LIST' will be ignored by grub anyway as it starts with a # which denotes a comment.

It could be that the win line starts with a capital 'T' in 'title' instead of a lower case 't' like the rest, thats a wild stab though.

---

### Post by weedwacker on 2008-07-02
> **danwood76 said:**
> Well it looks like it should be fine.
All your mappings etc look correct and partition numbers etc.

Are you sure you've scrolled all the way to the bottom of the list?
A guy in another thread hadn't done so, but you dont really have enough entries for that to be the case.

The '### END DEBIAN AUTOMAGIC KERNELS LIST' will be ignored by grub anyway as it starts with a # which denotes a comment.

It could be that the win line starts with a capital 'T' in 'title' instead of a lower case 't' like the rest, thats a wild stab though.

[COLOR="Blue"]THAT WAS IT!!![/COLOR] Thank you, Danwood76!!!:popcorn:

Changing the windows line word 'title' to a lower case 't' did the trick.

I'm pumped now!!! Thank you multiple times!!!

---


---
title: "Removing Ubuntu..."
date: 2007-09-01
forum: General Help
---

### Post by Orangepenguin on 2007-09-01
So Im trying to dual boot between WinXP and Ubuntu, and I cant seem to figure out how to uninstall Ubuntu.  I want to remove Ubuntu, install windows, and then reinstall Ubuntu.  When I put my windows disk in and boot from CD, nothing happens.  What do I need to do in order to remove Ubuntu?

---

### Post by HermanAB on 2007-09-01
What do you mean 'nothing happens'?  If it won't boot the Windows CD, then you have to change your BIOS boot settings - press Del or F2 during power up to get to the configuration screen. 

Windows should have no trouble erasing the partition table and reformatting the disk.

Cheers,

Herman

---

### Post by Orangepenguin on 2007-09-02
When you say to change my boot options, you just mean to change it to boot from "IDE CDROM" as the first boot device correct?  Because I have done this and it still just boots straight into Ubuntu.

EDIT: Okay I shouldnt say it does nothing.  It says "Press any key to boot from CD" (and I press keys and nothing happens) then it waits a few seconds, and then GRUB starts and Ubuntu loads.

---

### Post by fd9_ on 2007-09-02
> **Orangepenguin said:**
> When you say to change my boot options, you just mean to change it to boot from "IDE CDROM" as the first boot device correct?  Because I have done this and it still just boots straight into Ubuntu.

EDIT: Okay I shouldnt say it does nothing.  It says "Press any key to boot from CD" (and I press keys and nothing happens) then it waits a few seconds, and then GRUB starts and Ubuntu loads.

Just a long guess, but if you have a DVD slot and a CD slot, try putting it in the DVD slot. I remember I was having a similar problem, and my machine booted from the DVD slot.

Are you sure the Windows CD is good? It might have trouble reading it or something.

---

### Post by mikewhatever on 2007-09-02
Not sure about the boot problem, but you do not need to remove Ubuntu to reinstall either XP or Ubuntu. If you do not want to change the partitions, simply format the one for XP and install it, then, do the same with Ubuntu, if you wish to reinstall it too.

---

### Post by Orangepenguin on 2007-09-02
I only have one but its a CD/DVD slot.  Hmm do I need to remove GRUB or something?

---

### Post by SPr on 2007-09-02
> **Orangepenguin said:**
>  Hmm do I need to remove GRUB or something?

No. Windows will write over GRUB.

I would reinstall Windows but leave the Ubuntu partition as it is; I wouldn't format or reinstall anything on that partition.

1. Make a boot up disc using [Super GRUB Disc](http://supergrub.forjamari.linex.org)
2. Reinstall Windows.
3. Shutdown
4. Boot from the Super Grub Disc
5. Follow the prompts in the boot disc
6. The Super GRUB Disc will find both Windows and Ubuntu and everything will be set up automagically

Read the Super GRUB Disc docs first, of course.

---

### Post by Orangepenguin on 2007-09-02
Well, the problem is that i cant reinstall windows.  Thats basically what I am trying to do.  I doubt my windows disk is bad because I used it recently and I even have 2 and neither worked.

---

### Post by Orangepenguin on 2007-09-02
Ive tried all of these things and I cant seem to get Windows back on my PC... anyone else have any suggestions?

---

### Post by merlinus on 2007-09-02
If you cannot boot from you windows cd, then a number of things may be wrong.

Check BIOS to make sure cd is selected in boot order before hard disk.

CD drive may be defective or need cleaning, especially if the cds work on other machines.

There should be no problem reinstalling windows, no matter how your hdd is formatted or partitioned.

OTOH, perhaps there is a message for you in all this.... 

:)

-merlin

---


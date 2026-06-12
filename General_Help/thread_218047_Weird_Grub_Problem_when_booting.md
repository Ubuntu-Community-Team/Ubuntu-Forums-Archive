---
title: "Weird Grub Problem when booting"
date: 2006-07-18
forum: General Help
---

### Post by CameronCalver on 2006-07-18
Hello my computer was going fine till i turned it on today when it says grub loaidng it waits a couple of second then this comes up

```
Gnu Grub version 0.97

{Minimal  BASH-like  line edditing  supported. For
the first word,TAB lists possile command 
completions.Anywhere else TAB lists the possible
completions of a device /filename. )
grub>
```

Um im not sure what that meen so can someone plz help me

---

### Post by coffeecat on 2006-07-18
That's the grub prompt. Think of grub as a mini operating-system - a really mini one, perhaps a nano one. :) But you shouldn't get that unless you press 'c' (if I remember correctly) when you are presented with the boot menu. The grub prompt is available for when you need to pass special parameters at boot time. Not often needed in ordinary use.

Did you press any key when the boot menu appeared? Have you tried booting up again? Does it happen each time?

If you are still getting the problem you might need to look at/edit /boot/grub/menu.lst and/or reinstall grub. Neither is difficult and there are plenty here who can tell you how, but I can't understand how grub could have been changed if you didn't do anything.

---

### Post by CameronCalver on 2006-07-18
well i did not click c so how do i reinstall grub

---

### Post by CameronCalver on 2006-07-18
ok now it is comming up with grub error 18  and i understand that is a common error so how will i fix it

---

### Post by coffeecat on 2006-07-18
According to the Grub manual, error 18 is:

> 18 : Selected cylinder exceeds maximum supported by BIOS

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 
which can happen when grub is trying to read a block in a large hd beyond the 32GB limit with a BIOS that cannot handle hard drives larger than 32GB (for example). But if you haven't changed any hardware recently I can't at the moment explain this.

Before we try to reinstall Grub we need **much** more information, as follows:

1 Details of hardware, particularly how many and sizes of hard drives.

2 Your partition layout, including your Windows one of you've got one. If you're not sure, boot up with the Ubuntu live CD and look in System > Administration > Gnome Partition Editor. Be careful - don't change anything.

3 The contents of /boot/grub/menu.lst on your Ubuntu installation. You can use Ubuntu live to get this.

**Edit** For you to get grub doing something unexpected and then giving an error suggests a hardware problem - if you haven't been doing anything to the system. Perhaps a failing HD. I really don't know - I'm guessing here. How old is the machine?

---

### Post by CameronCalver on 2006-07-18
im not sure how old the computer system and
the size of the first hd is 160gb and it has windows on it and it has a partion called winlin which is 30gb and the linux hd is 40gb the partions are attached

and as for the menu.lst i attached it

---

### Post by coffeecat on 2006-07-18
You have a major problem in your menu.lst. Goodness knows why. Are you sure you didn't do anything to the hardware just before this happened? Anyway:

> title        Ubuntu, kernel 2.6.15-23-386
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot 
is the stanza to boot up Ubuntu. The line 'root (hd1,0)' is Grub syntax pointing to sdb1 (or hdb1) in Linux-speak - which doesn't exist - according to the partition information you gave. :? And then we have 'root=/dev/sda1' in the kernel line which is correct, but which contradicts the root line.

And then:

> title        Windows NT/2000/XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1 
is telling grub that Windows is on sda1/hda1, whereas you say it is on hdc1. (Grub, by the way, doesn't distinguish between ide and sata/scsi drives - they're all hd..something.)

The obvious next step is to edit menu.lst, but I'm unhappy to suggest this until we've found the reason for the discrepancies. The old adage about digging a hole applies here.

For what it's worth, the grub convention for numbering disks and partitions starts from zero, so hda1/sda1 becomes (hd0,0) and hdc1/sdc1 becomes (hd2,0), and so on. If you want to edit menu.lst you'll need to correct all root lines (and check the kernel lines), but do so at your own risk. This is a big mystery and I don't like solving problems if I don't understand the reason for the problem in the first place.

Anyone else have any thoughts?

---

### Post by CameronCalver on 2006-07-18
well do you think you can just tell me what i should have for my new menu list

---

### Post by CameronCalver on 2006-07-18
ok now when i boot up it does not say grub error 18 it now just says
grub> something is very wrong i think becuase grub is on the windows drive i should format the windows drive and install it again and install grub on the linux drive do you think that is the best way

---

### Post by blip on 2006-07-21
Don't know if it will help but I had a similar problem a while back.  Basically what was happening was that my MBR had gotten screwed up.  After repairing it (I used fixmbr from the Windows recovery console but I'm sure there is a linux equivalent) and reformatting the drive (it was my windows partition) all I had to do was reinstall grub which has happily worked ever since.

That said, your problem may not be so radical!  Mine was the result of a flubbed disk ghost restoration... so unless you did something similar, it may be a much less difficult problem to fix.

Have you tried booting up with a live disc and reinstalling GRUB?  It might be worth a shot and shouldn't make things any worse.

---

### Post by CameronCalver on 2006-07-21
yes that would be alot easyer and i did not think i have any problems with hardware and how do i reinstall grub from live cd

---


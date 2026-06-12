---
title: "Where did XP go?"
date: 2006-08-04
forum: General Help
---

### Post by foolsh on 2006-08-04
ok folks here is the story

   I get home this morning and see that some updates are avilable so after checking my sources.list file to make sure i didn't leave anything untrustworthy in there, I updated noticing that there was a kernel upgrade. I thought cool a new kernel I wonder if any new hardware drivers are added. that aside after reading the daily WTF and hack-a-day I decide to boot over to windows and spend sometime playing myst III - exile. It is BTW the only reason XP still exists on my computer. on reboot I am met with a nice list of.... whats this linux kernels and no windows option. grub didn't find one on the last kernel update. so I open /boot/grub/menu.lst and sure enough no windows.

i think the list of kernels got to long and grub short changed me.
now to re-enter the windows info into menu.lst


here is what i have so far

title		WindowsXP
root		(hd0,1)
makeactive
chainloader	+1
boot

title		Ubuntu, kernel 2.6.15-26-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

it spat out an error and I loaded ubuntu and came straight here.
I'm gonna try some more things and be back if anyone knows something useful dont be shy and let me know ... please

---

### Post by Ramses de Norre on 2006-08-04
This should do:```
title           Windows XP
root            (hd0,1)
savedefault
makeactive
chainloader     +1

```
Make sure you've got the right partition after root, it start's counting from 0 and should be the partition that's C in windows.

---

### Post by foolsh on 2006-08-04
thanks for the speedy reply but im still having trouble

here is a list of my partitions

/dev/sda2 as /
/dev/hda1 as /shared
/dev/sda1 as /windowsxp

should the (hdx,x) be (sdx,x) since its a sata drive?
is there a command for re-initizing grub to redetect my operating systems?

man this sucks
thanks again

---

### Post by Ramses de Norre on 2006-08-04
(hd1,0) should do then.

---

### Post by darrenm on 2006-08-04
So you have:

XP on a partition at the start of your SATA drive.
Ubuntu root partition on the next partition on the SATA drive.
and /shared as the only partition on an IDE drive?

If so your XP boot partition should be (hd1,0) and Ubuntu (hd1,1)

---

### Post by foolsh on 2006-08-04
title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

 stops with this error
filesystem type unknown, partition type 0x7

I think i remember something about swap 1 or something similar at the end of the code. see when i was installing the operating systems i had problems with booting so i tryed many different things and configurations. the harddrive that boots is hd0 but sd0 holds the operating systems.

maybe i'll boot the xp install disk restore the MBR then boot the ubuntu cd and initize grub i dunno good thing i dont work tonight.

---

### Post by foolsh on 2006-08-04
well after doing some soul searching and fasting... actually i went to the mall and checked out the girls it is friday after all.... i did some research (why is it called research when its the first time i SEARCHED for it?) and solved my problem the code is thus:

title           Windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1
map (hd0) (hd1)
map (hd1) (hd0)

I dont know where i got swap 1 from oh well on to myst 
thanks darrenm and Ramses de Norre

---

### Post by ifokkema on 2006-08-04
> **foolsh said:**
> is there a command for re-initizing grub to redetect my operating systems?
Actually, Yes.
```
sudo update-grub
```
It should find your Windows drive as well, and it's run after each kernel upgrade/install/uninstall.

---


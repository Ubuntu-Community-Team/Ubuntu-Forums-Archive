---
title: "Get rid of WinXP Partition - but no CD drive!"
date: 2007-03-14
forum: General Help
---

### Post by sp1964 on 2007-03-14
Finally got Ubunto onto my Fujitsu B2131 (no bootable CD, PCMCIA or USB you see). Had to start with an early net install and play with my Broadband security but got there in the end, then went through numerous rounds of upgrades and fixes etc and finally onto the latest Ubuntu!

Now I'm there I want to bin the Windows partition/original-install and add the free space to my Ubuntu drive as the PC only has a 6Gb HDD and windows is taking up 3Gb of it (!).

PROBLEM IS I can't boot up gparted-on-CD or similar as this PC can't boot anything other than Floppy or internal HD. 

Question 1 then it: is there a floppy bootable partition manager I can use?

Question 2 is: can I just blow away windows partition when I do get a partition manager and other than edit grub menu to take windows off will Ubunto still boot and work Ok?

I'd hate to have to spend 2d again getting back to where I am now (but at least I'd have only Ubuntu on the PC I suppose .... let's call that 'Option B')

Thanks

---

### Post by omockler on 2007-03-14
I'm not a Ubuntu expert but you should be able to edit the partition from Ubuntu install you already have.  If Gparted won't let you do it, try using a command line partition editor like parted or fdisk.  When you go to the command line make sure you use the tools as a super user.

As for the second question, you will be fine as long as grub isn't stored on the windows partition.  As long as grub is still on your machine and your Ubuntu install is one of the options you should be ok.

---

### Post by Doug11 on 2007-03-14
> **sp1964 said:**
> Finally got Ubunto onto my Fujitsu B2131 (no bootable CD, PCMCIA or USB you see). Had to start with an early net install and play with my Broadband security but got there in the end, then went through numerous rounds of upgrades and fixes etc and finally onto the latest Ubuntu!

Now I'm there I want to bin the Windows partition/original-install and add the free space to my Ubuntu drive as the PC only has a 6Gb HDD and windows is taking up 3Gb of it (!).

PROBLEM IS I can't boot up gparted-on-CD or similar as this PC can't boot anything other than Floppy or internal HD. 

Question 1 then it: is there a floppy bootable partition manager I can use?

Question 2 is: can I just blow away windows partition when I do get a partition manager and other than edit grub menu to take windows off will Ubunto still boot and work Ok?

I'd hate to have to spend 2d again getting back to where I am now (but at least I'd have only Ubuntu on the PC I suppose .... let's call that 'Option B')

Thanks


This may help you
[http://www.ubuntuforums.org/showthread.php?t=382704](http://www.ubuntuforums.org/showthread.php?t=382704)

---

### Post by bks on 2007-03-14
I think you could reformat from the System menu. System => Administration => Disks and choose your Windows partition and click "Format".  I haven't tried it myself, but I've seen it there.

---


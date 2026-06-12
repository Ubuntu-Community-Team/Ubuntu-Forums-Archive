---
title: "Linux Images filling up boot directory"
date: 2015-05-14
forum: General Help
---

### Post by asearle on 2015-05-14
Hi Everyone,

I find that Linux images progressively fill up my boot directory and I have to periodically delete them in order to be able to install further updates.

This is a known issue and there are suggestions/solutions to help with the deleting ...

[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

These suggestions are fine for me but I have installed Linux (mostly Lubuntu) on several friends' PCs and find that I cannot expect them to carry out command-line actions to regularly fix the problem.

I had been hoping that there was/is a switch that I can set in update options somewhere to tell the system to automatically delete older images.  But I cannot find this.  Can anyone help me here because unless I can permanently fix this problem for my non-computer-literate friends, I will be reluctant to install Linux for them.

I hope that someone can give me tip here:  It will help me gain more converts to Ubuntu  ;-)

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by dino99 on 2015-05-14
maybe set a cronjob on a weekly/monthly basis

---

### Post by entw on 2015-05-14
```
sudo apt-get autoremove
``` should remove obsolete images. Works for me.

---

### Post by SeijiSensei on 2015-05-14
[http://ubuntuforums.org/showthread.php?t=2276860](http://ubuntuforums.org/showthread.php?t=2276860)

I encountered the problem with too many kernel images some time ago and posted a bug report.  At the time the developers were finishing up their methods for limiting the number of kernels to two.  On recent releases like 14.04, that seems to work pretty consistently.  So I'd make sure you have everyone on a relatively recent distribution, then clean out any remaining crap in /boot as described in the thread above.  After that you shouldn't be seeing these problems.

You can automate the autoremove process if you'd like.  Just add this line to /etc/crontab
```

* 3 * * * root apt-get autoremove

```
That will run autoremove every day at 3:00 am.  That's a good time for servers and other machines that run 24/7.  On desktop and laptop machines you might want to pick a time like noon.

I take it these are dual-boot machines you're discussing.  There's no need for a separate boot partition on machines that run only Ubuntu.

---

### Post by ajgreeny on 2015-05-14
I was about to ask why you have a separate /boot partition as it can be a real nuisance and more often than not ends up with your problem.

If you choose encryption or to use of LVM a separate /boot partition is essential, otherwise it's not worth the hassle.

I am not even sure that SeijiSensei's comment about dual booting needing a separate /boot partition is correct.  It certainly wasn't in the days of Legacy BIOS, and even now with UEFI, I don't think it is necessary.  You have to have a separate small fat32 EFI partition, but that is not the same thing at all.

---

### Post by SeijiSensei on 2015-05-14
I may well be wrong.  I always thought /boot should stand "above" the actual OS images and built dual-boot machines that way.  On modern systems with enormous hard drives, I usually allocate 256 MB to /boot which is large enough to accommodate four or five kernel images and associated files.

---

### Post by Bashing-om on 2015-05-14
Guys:

I too used to create separate boot partitions until these came to my notice:
> 
 **Boot** :
However, sharing /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything. You have a couple of options. The best in the long term, but the most work, is to back up your Gentoo install, using either a second drive or a pile of DVDs, and repartition the disk from scratch.
&&

If you want to install GRUB2 to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector.
source:[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig)


I continue to multi-boot, now-a-days on a desktop machine, And have had no problems leaving /boot in the default '/' partition. But, do keep old kernels cleaned out, regardless.

[INDENT][INDENT]all a process of learning 
[INDENT][INDENT][INDENT]in this our ever changing world
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by asearle on 2015-05-15
You guys are fantastic!  Many thanks:  I'll add that line of script to crontab.  Cheers and thanks  :-)

---

### Post by asearle on 2015-05-20
Hi Everyone,  I thought autoremove would fix the problem but it doesn't seem to remove the kernel images in /boot.  Could it be that this is for software images but not for kernel?  Thanks, Alan

---

### Post by asearle on 2015-05-20
> **SeijiSensei said:**
> [http://ubuntuforums.org/showthread.php?t=2276860](http://ubuntuforums.org/showthread.php?t=2276860)

At the time the developers were finishing up their methods for limiting the number of kernels to two.  On recent releases like 14.04, that seems to work pretty consistently.  So I'd make sure you have everyone on a relatively recent distribution, then clean out any remaining crap in /boot as described in the thread above.  After that you shouldn't be seeing these problems.



Limiting kernels to two sounds like the perfect solution.  I am running Lubuntu 14.04 (rather than Ubuntu) and although I seem to have the correct/newer version the Kernels are not being cleaned out.  I'd like to stay with the Long-term-support version so is there anything I can do to get this working?  Or is Lubuntu simply not quite as up-to-date as Ubuntu?

Many thanks,
Alan Searle
Cologne

---

### Post by ian-weisser on 2015-05-20
The code for autoremoval of old kernels is identical in Ubuntu, Lubuntu, and all other official flavors.

Is /boot currently full, preventing the package manager from working?
Does a manual 'sudo apt-get autoremove' work?

---


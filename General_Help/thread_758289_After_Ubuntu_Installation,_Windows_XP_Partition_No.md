---
title: "After Ubuntu Installation, Windows XP Partition Not Recognized!!! Please Help!!!"
date: 2008-04-17
forum: General Help
---

### Post by Hereje on 2008-04-17
Hello everyone, well the whole problem is this, I really would appreciate any help...

I have 2 HD's installed on my PC, one 300gb sata just for data, and one 80gb IDE, this one partitioned this way: 40gb NTFS partition with Windows XP installed, 39.5 gb EXT3 partition, 512mb SWAP Partition.

Today i've downloaded Ubuntu 8.04 b4 and installed it in the EXT3 Partition, the idea was to dual-boot with windows XP, when Ubuntu Installation asked where to write the Grub for Dual-boot (i think) I chosed the partition with windows Installed, because It was the first... 

Well, now when in GRUB I try to get into Windows XP it says there's a file missing ntoskernel.exe or something and i have to reinstall but when I tried to do it shows me the partition with a unrecognized file system, so i didn't try it.

Back to Ubuntu, it recognizes the other Hard Disk with its partitions, but the windows XP main partition where a whole of important files are, don't recognize it...

Gparted shows the partition with a (!) Next to it, and says that "is impossible to read the content of this file system. some operations may not be available"....

I don't wanna lose the data in that hard Disk!!! Please!!! Help me!!!

---

### Post by LeoSolaris on 2008-04-17
Ok what you did was write Grub over XP's boot space. It should be fixable by putting the XP install CD back in and doing a repair rather than an install. You will have to put Grub in the MBR (Master Boot Record) to dual boot. It should automatically set XP up with a chain load, meaning Grub hands off the loading to XP's bootloader to complete the booting process, rather than booting entirely with Grub, like Ubuntu does. You wrote over a portion of XP, most likely that bootloader that Grub has hand off booting to for XP to load.

Leo

---

### Post by Hereje on 2008-04-17
Thanks for your help, is there another way to do that without the Windows XP CD? That's because I only have the Windows XP UE 7 version and it doesn't includes Recovery Console...

I'm downloading a complete version of windows just for try it, but i think it's gonna take long time...


Thanks.

---

### Post by Reg Editor on 2008-04-17
you can download the recovery console,burn it to a cd using the option copy image to disk,or the option burn iso.if you havent got  suitable burning software use 

[http://www.snapfiles.com/get/silentnightcd.html](http://www.snapfiles.com/get/silentnightcd.html)

direct download link [http://www.thecomputerparamedic.com/files/rc.iso](http://www.thecomputerparamedic.com/files/rc.iso)

---

### Post by bodhi.zazen on 2008-04-17
You can restore the windows boot loader from within linux, using the Ubuntu or Knoppix :

[http://ubuntuforums.org/showpost.php?p=4691608&postcount=2](http://ubuntuforums.org/showpost.php?p=4691608&postcount=2)

---

### Post by Hereje on 2008-04-18
Hey!!!! Thank you guys for the help!!!!

Downloaded the Recovery Console and did FIXBOOT, after that did CHKDSK /R. So I could save my files...!!

Now I've finished installing Windows XP and Ubuntu 8.04 in the same hard disk and everything works great!!!

Thanks for your time!!!

What would be of us without sharing information?

Bye!!!

---


---
title: "What is the Grub Line for Feisty?"
date: 2007-05-26
forum: General Help
---

### Post by Nameless on 2007-05-26
I ask this question because I recently reinstall PCLOS 2007 on anther partition and when it installed grub (its own graphical version) it overwrote my old grub and apparently all the entries in it.  Surprisingly, it was able to find the windows partition correctly, just not my Ubuntu one.  I want to edit my grub menu manually now, but I can't figure out what I need to put in the /boot/grub/menu.lst in order to make Fiesty one of the boot options. 

Here's my drive set up:
Hda - Windows
Hdb - Ubuntu (I know it the generic kernel, but I don't know what number)
Hdc - Empty
hdd - PCLOS 
hde - swap

Thanks...Nate

---

### Post by ffi on 2007-05-26
hard to say with that uuid thing ubuntu uses, easiest way i think would be copy the entries for feisty from feisty's grub to pclinuxos' grub  (each in /boot/grub/menu.lst on the respective partition)

---

### Post by Nameless on 2007-05-26
Oh, I didn't realize that grub would be installed on each partition, I just figured it was only on the first partition.  I'll give that a try when I get home.  

That leads me to another question: 

How does the computer know which grub to use?

---

### Post by ffi on 2007-05-26
> **Nameless said:**
> Oh, I didn't realize that grub would be installed on each partition, I just figured it was only on the first partition.  I'll give that a try when I get home.  

That leads me to another question: 

How does the computer know which grub to use?

I am not quite sure but I believe the grub part on the mbr just points to a directory on some other partition of choice, I think pclinuxos install changed that from pointing to feistys /boot/grub to pclinuxos /boot/grub

---

### Post by confused57 on 2007-05-26
> **Nameless said:**
> Oh, I didn't realize that grub would be installed on each partition, I just figured it was only on the first partition.  I'll give that a try when I get home.  

That leads me to another question: 

How does the computer know which grub to use?

You could reinstall Feisty's grub to the boot hard drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then you could add an entry to your Feisty /boot/grub/menu.lst to boot PCLinuxOX, using configfile:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)
or you could use the live cd to install PCLinuxOS grub to the root partition & use chainloading.

Whichever Linux distro you install last will install it's grub IPL code to the boot drive's(hd0) mbr, some distros are better at detecting other OS than others.

---

### Post by Nameless on 2007-05-26
ffi & confused, 

Thank you both for your help.  I was able to log into PCLOS and edit the /boot/grub/meun.lst file by copying the data from the same file on my Ubuntu partition.   Now I'm posting this from my Ubuntu partition.  

I didn't realize that there would be a grub folder on each partition.  I was also able to rearrange the entries like I had been planning to do for a while now.  I learned a lot about grub today.  Thanks again.

---


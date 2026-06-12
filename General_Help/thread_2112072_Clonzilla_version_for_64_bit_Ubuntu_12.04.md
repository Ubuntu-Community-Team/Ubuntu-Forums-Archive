---
title: "Clonzilla version for 64 bit Ubuntu 12.04"
date: 2013-02-03
forum: General Help
---

### Post by RogerDavis on 2013-02-03
It's happening again - the more I think I know, the less I really know.

I want to clone (bit to bit) my 1T drive to another 1T drive (2 exactly same drives), with ONLY Ubuntu 12.04 on it.  Both are internal drives, and can be mechanically switched on or off by turning off power to it.

It seems clear that I want the "Live" version.  If I choose the Debian version, I need the 64 bit one.

I see a Ubuntu version of Clonezilla, and a Debian version.  It is said that the Debian version might be based on an older kernel, and not be compatible with newer hardware.  My machine is only a few months old.  Also, common sense says "Ubuntu for Ubuntu" is best.  But the Ubuntu version is said to be less stable and could give problems after a few months.  I NEED this to be ready to go at any time and not have to worry ever few days or weeks about updating it.  All this is at  [http://drbl.org/faq/fine-print.php?path=./2_System/57_why_ubuntu_based_clonezilla_live.faq#57_why_ubuntu_based_clonezilla_live.faq](http://drbl.org/faq/fine-print.php?path=./2_System/57_why_ubuntu_based_clonezilla_live.faq#57_why_ubuntu_based_clonezilla_live.faq)  

So - Debian or Ubuntu version?

Also, there is some talk that some of the clone software may not be aware of the latest disk formats.

Or - is there a better bit-to-bit clone software?   If so, what is it?   What makes it better?   Where can I find it?

Thanks!

---

### Post by dcstar on 2013-02-05
> **RogerDavis said:**
> 
...........
Or - is there a better bit-to-bit clone software?   If so, what is it?   What makes it better?   Where can I find it?

Thanks!

Booting cloning software has no relevance for 32 or 64-bit as long as it matches the hardware you have. All they do is simply access the disk hardware. You can simply clone drives by using an Ubuntu Live CD/USB and using the "dd" command. You are over-complicating a very simple task.

Cloning entire disks always connected in a single system is a bad move as the boot loader will see two identical UUIDs for every partition on the disks and use the last one it finds (AFAIK) which may not be the one you want to be used.

---

### Post by RogerDavis on 2013-02-05
The disks are not always connected.  They are mechanically switched, and the cloned disk would be turned off afterward.

---

### Post by Cheesemill on 2013-02-05
Any version of Clonezilla should work.

---

### Post by orb9220 on 2013-02-05
> Or - is there a better bit-to-bit clone software? If so, what is it? What makes it better? Where can I find it?

For me found Clonezilla to confusing and difficult to figure out new to backing up partitions and such.

Found [Redo Backup]("http://redobackup.org/"). Uses same under the hood engine as Clonezilla with a much simpler user interface.
It's 250mb and just burn and boot with it. Simple Backup or Restore,Internet support,other tools.

I have backup up entire drive with Win7,Winxp & 3 linux partitions. And then backup just the linux partitions. That way can install complete distro's to try and setup. Then back those up. That way I can install any distro on the fly in about 20mins. Ubuntu 12.10,Mint Cinnamon 14,Mint KDE,Fuduntu.Voyager 12.10,Bodhi,etc..

Might be more to your preference.
.

---

### Post by RogerDavis on 2013-02-05
Redo looks good, but it isn't clear - free or $ ?   I can't find any info on this on the site.  I don't see anything asking for money, but nothing that says they won't...

---


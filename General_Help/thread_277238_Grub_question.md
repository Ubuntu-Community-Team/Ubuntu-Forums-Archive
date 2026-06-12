---
title: "Grub question"
date: 2006-10-14
forum: General Help
---

### Post by Familyguy on 2006-10-14
I have xp on hd0 and dapper on hd1.
I have tried the super grub disk fix.The fix is listed as sucessful but when I reboot it hangs at "Boot from CD".
Grub was working before I upgraded windows 98.
Using the UBCD i am able to boot both OS's using Smartboot.
I booted into Dapper this way and ran the grub setup.
I got the same problem as before.
Here is what I did,
 grub> find /boot/grub/stage1
Reports hd 1,0
I then enter  grub> root (hd1,0)
grub> setup (hd0)
Should I be entering (hd0,0) here?
Anything else I should try?
I figure I all most have it working but I don't want to mess anything else up trying another fix.

---

### Post by alecjw on 2006-10-14
Are you sure that you mean hd0 and hd1? Do you mean that they are on different partitions or different physical drives?

---

### Post by Kateikyoushi on 2006-10-14
Let there be no doubt about it, list your partitions with the following.

```
sudo fdisk -l
```

---

### Post by Familyguy on 2006-10-14
I have 2 hard drives.Win XP on the 1st and Kubuntu on the 2nd.

/dev/hda1   ntfs
/dev/had2   w95 Ext'd (LBA) 
/dev/hda5   ntfs


/dev/hdb1   Linux
/dev/hdb2   w95 Ext'd (LBA) 
/dev/hdb5   lINUX swap
hda1 and hdb1 are listed as Boot (*)
hda is 160 GB
hba is 40 GB

---

### Post by Kateikyoushi on 2006-10-14
What is your boot order in the bios ?

---

### Post by Familyguy on 2006-10-14
boot order is 
cd rom
hd0
hd1

---

### Post by randell6564 on 2006-10-14
> **Familyguy said:**
> I have xp on hd0 and dapper on hd1.

No, you have XP on hda1 and Ubuntu on hdb1.
> Here is what I did,
grub> find /boot/grub/stage1
Reports hd 1,0
I then enter grub> root (hd1,0)
grub> setup (hd0)
Should I be entering (hd0,0) here?
No. I believe that you would enter,```
setup (hd1)
```

---

### Post by peeps on 2006-10-14
Have you tried Tomosaur's script, to edit the Grub options?  It's far easier than doing it by hand.

[http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd.zip](http://www.ubuntuforums.org/showthread.php?t=228104&highlight=GrubEd.zip)

"It's the best thing since sliced bread".:D  Well for a noob like me it is anyways.

---

### Post by Familyguy on 2006-10-17
I got it to work again.
Using the Universial Boot CD, I booted in to Ubuntu using Smartboot.
The then opened a terminal and typed "# grub-install /dev/hda" .
[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

---


---
title: "help, i can't boot GRUB without an external HDD plugged in"
date: 2008-02-05
forum: General Help
---

### Post by nabxf on 2008-02-05
now before people start bashing me for not looking at other threads, i did.
also googled, yahooed, etc.

i have a dell e520, same as my dad.
i installed ubuntu on my ipod mini as an external hard drive, so as not to mess up the drive inside my computer.
being a linux noob, i didn't back up my mbr, and now i can't boot without the ipod plugged in (i'm getting the whole "grub 1.5 failed" thing)

everybody has suggested using fixmbr from the windows recovery disk, where i have searched
however, i was speaking to a friend of mine whose dad works for dell and it turns out the dell use a different mbr from other computers, and restoring xp's default mbr will just blue-screen me everytime i boot.

so what i would like to know is, **is it possible to either bypass the GRUB boot and leave my mbr untouched, or is there some way to restore a dell computer's mbr without any of the standard fixes like mbrfix.exe and fixmbr?**

thanks for your help everybody!

---

### Post by agim on 2008-02-05
You can't bypass grub to get to your mbr because grub overwrote your mbr. But there is a fix.
There is something called the super grub disk. according to its website:
You can not boot Windows because your MBR is corrupt or Grub installation is not well done or whatever. With Super Grub Disk you will be able to boot the partition where Windows reside.
Here is the website.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Maybe from there you can write to the mbr so you don't need the disk each time.

give it a try, if you have trouble with that write back and we can go from there.

---

### Post by agim on 2008-02-05
Here is a good tutorial for it.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Hope this helps.

---


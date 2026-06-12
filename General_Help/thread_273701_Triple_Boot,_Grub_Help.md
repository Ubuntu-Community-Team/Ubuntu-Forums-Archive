---
title: "Triple Boot, Grub Help"
date: 2006-10-08
forum: General Help
---

### Post by TheIdiotThatIsMe on 2006-10-08
Sorry in advance, I know these kind of problems pop up all the time.

I originally had Ubuntu on a 12GB partition on my HD, with another 60g partition that I formatted. The 60g was formatted into several partitions, including a 20g with wich I installed Windows XP on, and then another 20g with which I installed Fedora Core 5 on. However, when installing I had to delete the swap I originally had for Ubuntu so I could make a new primary partition for Fedora Core 5, and then recreated it which caused Fedora Core 5 to create an extended partition and create the linux-swap in that.

So my setup looked like this, according to Fedora Core 5:

HDA1 -> Windows
HDA2 -> Fedora Core 5
HDA3 -> Extended
HDA5 -> Linux-Swap
HDA4 -> Ubuntu

Now when I boot up the computer, I can currently get into Windows XP and Fedora Core 5 just fine, however I use Ubuntu as my main work machine and only wanted to install Fedora Core 5 since my campus uses it as it's Linux OS, and I had never played with a Red Hat distro. I set up Grub in Anaconda to boot according to the partitions as shown above as Fedora Core showed them, with the default to boot Ubuntu.

Unfortunately, when I attempt to boot into Ubuntu, I get the error:

```
Booting Ubuntu

rootnoverify (hd0,3)
Chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue...
```

How do I get Ubuntu to boot again :confused:

---

### Post by Kateikyoushi on 2006-10-08
You should remove the chainloader +1 line.
Also you need to add a line which points to your kernel

An example.

```
title		Linux
root		(hd0,1)
kernel	/vmlinuz root=/dev/hda2 ro

```

You can get this from your ubuntu partition's /boot/grub/menu.lst
If you changed the partitions have to edit it so the entries to point to the current partitions.

---

### Post by TheIdiotThatIsMe on 2006-10-08
Sorry, but how do I go about removing the chainloader and changing the information?

---

### Post by TheIdiotThatIsMe on 2006-10-08
Thanks for the help. I was able to get it to the bootscreen for ubuntu, but it now hangs at "Mounting root filesystem'. Any idea how to get it to mount at hda4 for root? i thought I changed the right setting but apparently not :confused:

---

### Post by tommcd on 2006-10-09
You might try to restore grub from the live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)
Or if you have an alternate CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
Hope this helps.

---


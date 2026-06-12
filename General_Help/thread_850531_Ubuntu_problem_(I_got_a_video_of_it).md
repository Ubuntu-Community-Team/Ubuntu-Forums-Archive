---
title: "Ubuntu problem (I got a video of it)"
date: 2008-07-05
forum: General Help
---

### Post by oib111 on 2008-07-05
Well basically I dual boot windows and ubuntu, but whenever I go into windows and then try ubuntu I go to this weird shell. Anyway...I finally got back from Hawaii (not like I wanted to come back) and there was a power outage so my computer had automatically booted into Windows (after the outage) and so Ubuntu's ****** again (it happened like 5 times before). But I got a video of it. So [here it is]("http://rapidshare.com/files/127393284/100_1515.rar.html"). It includes a .mov file that shows the bootup. Sorry about the bad filming, I just got back from an overnight flight x_x

If you can't see what the shell says. It says:

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 

```

---

### Post by Sam Lars on 2008-07-05
Have you tried selecting the (safe mode) option from the Grub menu?
Also, reinstalling Ubuntu may be a good thing to try.

---

### Post by oib111 on 2008-07-05
There's a safe mode in the grub menu? Lol, I didn't know that. I'll try. And also I have to reinstall every time I get this error. And I've used about 3 different CD's with the same ISO for about 5 reinstalls. But I'll try the safe mode.

---

### Post by oib111 on 2008-07-06
That didn't work. It just got stuck at one driver.

---

### Post by jocko on 2008-07-06
I'm guessing that's a wubi install?
(I saw you had the windows boot menu before grub and ubuntu is on an ntfs file system...)
In that case maybe you should ask in the wubi section of the forum (or have this thread moved there)?

When you boot ubuntu, is windows xp *properly* shut down?
If xp is just hibernated or the file system is not properly unmounted from windows, the ntfs file system will probably not be fully accessible from another os.
Have you tried running "chkdisk /f" from a windows command line? Maybe you have some file system corruption...
Another thing I can think of is that perhaps XP (or a virus/any other software you have installed on it) makes some changes to the file(s) that contains the wubi install, making it fail to boot...
Ever thought about making a real ubuntu install on a native linux file system?

---

### Post by rubicon on 2008-07-06
That usually means you should check your root filesystem. Simply said, Busybox is just little *shell* stored in kernel image, activated only if you have problems with your /bin/sh (for example, filesystem containing it wasn't clearly unmounted).

Try to run ```
fsck -y /dev/sda1
``` where *sda1* is partition you have installed ubuntu onto and then reboot. If it fails and tells you something like 'cannot check ntfs filesystem', try different sdaX (type 'fsck -y /dev/sda' and press TAB twice to see list of possible variants)

---

### Post by jocko on 2008-07-06
> **rubicon said:**
> That usually means you should check your root filesystem. Simply said, Busybox is just little *shell* stored in kernel image, activated only if you have problems with your /bin/sh (for example, filesystem containing it wasn't clearly unmounted).

Try to run ```
fsck -y /dev/sda1
``` where *sda1* is partition you have installed ubuntu onto and then reboot. If it fails and tells you something like 'cannot check ntfs filesystem', try different sdaX (type 'fsck -y /dev/sda' and press TAB twice to see list of possible variants)

That would only do it if he actually had ubuntu on it's own file system, but he seems to use wubi, so ubuntu is on an ntfs partition. So he needs to run a windows chkdisk...

---

### Post by rubicon on 2008-07-06
> **jocko said:**
> That would only do it if he actually had ubuntu on it's own file system, but he seems to use wubi, so ubuntu is on an ntfs partition. So he needs to run a windows chkdisk...
Geez, I never thought that using wubi is *this* different than natural dual boot %)

Well then, disregard my last post.

---


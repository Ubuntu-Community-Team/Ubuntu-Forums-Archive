---
title: "GRUB error, and computer poblem"
date: 2007-03-27
forum: General Help
---

### Post by tjl30 on 2007-03-27
_The last 3 times I started my computer, the following happend:_
1.  I get to the bio's momentarily, then enter GRUB
2.  Once in grube I get this
```
GRUB Loading stage1.5.
GRUB loading please wait...
Error 17
```
3. So I Inserted my Ubuntu 6.10 Server disk and restarted my computer.
4. Then it boots to the disk, I select Restore Broken System, then choose /dev/hdb1, then Reinstall GRUB boot loader, then I hit continue and then it says Rescue operation failed. 
5. From there I reboot the system, remove the CD before it loads, and the computer boots up fine. It starts up GRUB without error and I am able to boot into Ubuntu 6.10. Now the problem is I have to do this every time I start my computer. 

If anyone could help me fix this problem that would be great! I also just recently added Ubuntu 6.10 Server to my computer, but I usually boot into Ubuntu 6.10 (Which I recently upgraded to from 6.06).

---

### Post by jimbob on 2007-03-27
Error 17 indicates that GRUB cannot recognize the file system type.

Which partition is it trying boot?  Try starting grub from a recovery disk and enter the boot commands manually as found in your menu.lst and see if it still has a problem.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by tjl30 on 2007-03-27
Partition       Filesystem         Size              Flags 
/dev/hdb1     ext3                   59.7GiB
/dev/hdb3     ext3                   12.83Gib     boot
/dev/hdb2     extended          2Gib
--/dev/hdb6     linux-swap     596.1Mb
--/dev/hdb5     linux-swap     1.42GB

For some reason the HD in my computer (The only one) is recognized as hdb.

---

### Post by confused57 on 2007-03-27
> **tjl30 said:**
> Partition       Filesystem         Size              Flags 
/dev/hdb1     ext3                   59.7GiB
/dev/hdb3     ext3                   12.83Gib     boot
/dev/hdb2     extended          2Gib
--/dev/hdb6     linux-swap     596.1Mb
--/dev/hdb5     linux-swap     1.42GB

For some reason the HD in my computer (The only one) is recognized as hdb.

You can try different root combinations from your boot grub menu, by highlighting the Ubuntu entry, press "e" to edit, then try changing root to (hd0,2) or (hd0,0), then press "b" to boot.
This change is temporary, but you can make it permanent in your /boot/grub/menu.lst if it works:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo nano menu.lst
```
ctrl+x, y, "enter" to save

You can also use the grub CLI to investigate your computer:
[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

---

### Post by tjl30 on 2007-03-27
When I did that I only saw one system that I could boot into, that was (hd0,0) but I have two partions. Is it possible that I have two grub loaders and one gives the error and the other one works?

---

### Post by tjl30 on 2007-03-31
I fixed the problem. There is a diagram on my HD that shows where to put the jumpers, it read this diagram upside-down so the jumpers where in the wrong spot. This made my computer think my main HD was /dev/hdb, the problem was when booting my computer would first not find the IDE, then when I re-booted it found it.

After this grub would start-up and get an error. So I put the jumper in the right space so the computer sees the HD as the master drive /dev/hda. Then I booted up a live distro (ubuntu 5.10) and edited grub in terminal (changed all the things that said hdb1 hdb3 ect to hda1 hda3 ect. After that ubuntu could load, and now I no longer get any problems.

---


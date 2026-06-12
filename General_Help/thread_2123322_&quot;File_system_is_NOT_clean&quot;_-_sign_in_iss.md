---
title: "&quot;File system is NOT clean&quot; - sign in issue"
date: 2013-03-07
forum: General Help
---

### Post by lonewolf88 on 2013-03-07
Lubuntu 12.10 (?) dual boot with Win 7. Toshiba notebook sort of thing.

Since the upgrade to 12.10, can no longer log in, screen keeps coming back for username and login details repeatedly.

Booted into rescue mode, ran a few commands found by doing the usual Google searches, still not able to log in.

Confirmed user name and changed password as per these commands.

Now in rescue mode get error message "File system is NOT clean" (next line) File system seems mounted read-only".

Maybe this is the cause of my issues?

How do I make the file system "clean", and what else do I need to do?

As usual, thanks in advance!

---

### Post by kclark on 2013-03-07
Have you run [fsck]("http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html") on the disk yet?  What were the results?

---

### Post by lonewolf88 on 2013-03-08
Thanks, rang fsck, No corruption reported, except at beginning:-

"File system seems mounted read-only.
Skipping journal replay"

This is in spite of running

mount -o remount, rw/
sync
reboot -f

which I found on a few sites as a read only work around.

---

### Post by sudodus on 2013-03-08
I suggest that you boot from another drive, for example from your Lubuntu CD/USB install drive.

Then identify the system partition for your installed Lubuntu system with the following commands

```
sudo fdisk -lu
```
```
sudo blkid
```
Check with 
```
df
```
that the system partition for your installed Lubuntu system is not mounted. If it is mounted unmount it with
```
sudo umount /dev/sdxy
```
where x is the device letter (a for the first drive, b for the second one ...) and y is the partition number (1 for the first partition, ..., 5 for the first logical partition ...)

Post the result of the previous commands if you need help to identify the root partition of your installed system!

Then run e2fsck to check and repair the file system
```
sudo e2fsck -f /dev/sdxy
```

If you have a separate /home partition, you might need to check it in the same way too.

---

### Post by lonewolf88 on 2013-03-08
Thanks for the above, unfortunately cannot boot from any installation cd (see thread[ Toshiba T110  - dvd hangs on install]("http://ubuntuforums.org/showthread.php?t=1643874"). dated 2010. (Don't ask how I finally managed to install, I must have fluked it!).

So ran the command from root in the boot up rescue for 12.10 on the Toshiba.  Mounted on fda4.

Error message "The superblock could not be read or does not describe a correct ext2 filesystem"

Fritzed?

---

### Post by sudodus on 2013-03-08
If you cannot boot from CD, you probably booted and installed from a USB drive (pendrive or HDD). Could you do that again? Because it is strongly recommended for e2fsck to operate on an unmounted device. Read
```
man e2fsck
```

---

### Post by lonewolf88 on 2013-03-08
How about I try from a "free this month" cd on a linux mag.  Would that do it?  What I had in mind run the cd in demo mode under Windoze and see if I can open a terminal?

---

### Post by sudodus on 2013-03-08
You can always try to boot directly or under Windows with such a linux CD. If it has e2fsck (and it should), and if it can see the linux file system, it should work.

---

### Post by lonewolf88 on 2013-03-10
Apologies for late reply.

Booted from "free" distro (magazine special). Errors received as follows

Bad magic number in superblock
Superblock invalid

I then ran the alternate suggestion to create a new superblock.

Superblock could not be read or does not contain a valid ext2
2 filesysytem.

Apologies for taking your time!  Anything else I can try except a complete re-install?

---

### Post by sudodus on 2013-03-11
Please explain in more detail:

What free distro is it?
When you boot from that disk, what can you do?

Can you 'see' the internal drive?
Can you 'see' any partitions on it?
Can you mount any partitions on it?
Can you read a file from any of the partitions?
Can you write a file from any of the partitions?

What about the lubuntu partition?
Can you 'see' it?
Can you mount it?
I guess you cannot read a file from it?
If mounted, can you unmount it?
Can you run
```
e2fsck -f /dev/sdxy
```
on the lubuntu partition?

At what instance do you get the output
Booted from "free" distro (magazine special). Errors received as follows
1.
> Bad magic number in superblock
Superblock invalid

and 2.
> Superblock could not be read or does not contain a valid ext2
filesysytem.

The reason I ask about these details is that I try to understand if the whole drive or only the lubuntu partition is bad, and in what way.

---

### Post by p_code on 2013-03-11
Hi, sorry to jump in here, but it sounds like you are barking up the wrong tree, trying to fix a severly corrupted installation that is just NEVER going to boot correctly.

The question that you should be looking at is WHY, it installed with a corrupted file system, and WHY it wouldn't boot cleanly from the installtion CD.

Here is a thread that explains some boot options which will change some Kernel settings, and *hopefully* give you a live session that boots cleanly and therefore can install cleanly.

You can find the information you need in this thread --

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For my laptop, the magic settings were nolapic, and nomodeset, but the same menu is also used to disable acpi=

Note the warning however, that on at least some laptops, disabling acpi  messes up the thermal management by killing the fan control.

Also I am not sure if you go ahead and do the install after using the  above cheat codes to boot, if the installer is then smart enough to  incorporate those settings into your permanent grub boot settings  (knowing Ubuntu, probably NOT).

So scan down through the thread and note how to PERMANENTLY change your grub settings.

This is a royal pain because you also have to do a little finger dance  and interupt your first grub boot, to supply the boot options manually  -- using a totally different sequence than with the live CD.

Without this, Ubuntu will probably crash, just as it does when booting the live CD without the codes.

The good news is that, once you manually supply the cheat code boot  options to grub manually the first time, you can edit the grub configuration  text file in Ubuntu, and then run grub to write the changes permanently to your  boot loader, and then Ubuntu should start seamlessly after that.

---

### Post by lonewolf88 on 2013-04-12
Thanks, and apologies for the late reply.

In the end I did a complete new install, the partitions were messed up, and I saved the good stuff first.

---


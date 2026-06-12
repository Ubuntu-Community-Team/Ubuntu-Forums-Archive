---
title: "Laptop will not boot after update - please help"
date: 2007-12-21
forum: General Help
---

### Post by mneisen on 2007-12-21
Hi, 

I updated my laptop (Samsung X20, running Kubuntu 7.10) today at around 12:00pm GMT. This update included a new version of the current kernel. Everything installed fine.

Tonight, I rebooted the laptop, and the boot process stopped very soon, the progress bar was still at the very left. After pressing Alt+F1, I could see the last message of the boot process: Something about the CD/DVD drive.

I tried to reboot several times, switching the laptop completely off every time. No luck ...

Can anybody guess what is wrong?

Alternatively: Does anybody know how I can get my laptop back to boot normally?

Thanks in advance!

---

### Post by p_quarles on 2007-12-21
First thing to do would be to log into recovery mode (from the GRUB menu) and check the syslog:
```
less /var/log/syslog
```
It should be able to tell you something about what's going wrong.

---

### Post by mneisen on 2007-12-21
> **p_quarles said:**
> First thing to do would be to log into recovery mode (from the GRUB menu) and check the syslog:
```
less /var/log/syslog
```
It should be able to tell you something about what's going wrong.

I just booted the Live CD and had a look at syslog; the last things in there are from before the reboot. I think the problem is that the boot stops after about 4 seconds, long before anything gets written to the syslog.

BTW: recovery mode does not work either. It hangs at the same point (something about the CD/DVD drive), it only takes a little longer to get there :-)

Any guess?

---

### Post by p_quarles on 2007-12-21
Okay, nothing in syslog. If it's failing that quickly after power-up, I would wonder if it's a hardware problem of some sort. Maybe try using the live disk to run fsck. 

Also, depending on how full-featured your BIOS is (i.e., if this isn't a Compaq), you might find some debugging tools in there.

---

### Post by mneisen on 2007-12-21
> **p_quarles said:**
> Okay, nothing in syslog. If it's failing that quickly after power-up, I would wonder if it's a hardware problem of some sort. Maybe try using the live disk to run fsck. 

Also, depending on how full-featured your BIOS is (i.e., if this isn't a Compaq), you might find some debugging tools in there.

No, I use a Samsung X20.

Plus, this is not hardware-related since the Live CD boots up perfectly.

The simple solution: the kernel update from this morning changed GRUB's menu.lst in a very marginal but still very crucial way: it messed with my root= boot flag.

My root partitions vol_id is 926efc98-7e18-4599-9e26-71cbbdd853c7, and this value was in menu.lst before the upgrade.

After the upgrade, the value in menu.lst (for both the "normal" boot entry and the recovery mode) had changed to 52bb200c-f962-40a9-9200-bc1ce963210b. None of the partitions on this laptop has this vol_id; i can only guess, but maybe some partition on the test/packaging system for the kernel upgrade has a partition with this vol_id.

I simply booted up using the Live CD, determined the correct(!) vol_id for my root partition, manualy mounted the boot partition and changed /boot/grub/menu.lst accordingly.

Now, everything is back to normal.

I consider classifying this as a serious bug and opening a ticket in launchpad.

You might wonder why I told at first that the error might be something about the CD drive.

This was simply the last line of output on the screen. 

You have to wait *really* long before the kernel prints out an error message about not finding the root partition with the UUID you gave it via GRUB's menu.lst. 

Fortunately, I did wait for a very long time because I copied down the boot output line by line to my notepad (no, not the Windows one ... :-D) so I can post it here. 

After about 2 mins, the kernel outputs an ALERT! line with the error message that got me on the right path.

---

### Post by p_quarles on 2007-12-21
Sweet. Glad you got it fixed. And I definitely encourage you to file a bug report. 

Btw, when I said hardware, I was specifically thinking of the hard drive. Running off the CD wouldn't necessarily run into any trouble if there were bad sectors. Obviously, that wasn't the problem, though.

---

### Post by mneisen on 2007-12-21
> **p_quarles said:**
> Sweet. Glad you got it fixed. And I definitely encourage you to file a bug report. 

Btw, when I said hardware, I was specifically thinking of the hard drive. Running off the CD wouldn't necessarily run into any trouble if there were bad sectors. Obviously, that wasn't the problem, though.

Now I see what you meant by HW problem. But still, the HD could not be the problem since I could boot everything from the Live CD - which I had not told. Sorry.

Thanks again for the help!

---

### Post by mneisen on 2007-12-21
> **p_quarles said:**
> Sweet. Glad you got it fixed. And I definitely encourage you to file a bug report.

BTW: Against which package should I file the bug in launchpad ?

---

### Post by p_quarles on 2007-12-21
> **mneisen said:**
> BTW: Against which package should I file the bug in launchpad ?
I'd say GRUB, probably.

---

### Post by meierfra on 2007-12-21
I don't think it is   bug.  Look at the line

# kopt=root=UUID=....

in menu.lst. It probably contains the wrong UUID.

---

### Post by p_quarles on 2007-12-21
> **meierfra said:**
> I don't think it is   bug.  Look at the line

# kopt=root=UUID=....

in menu.lst. It probably contains the wrong UUID.
Yeah, the fact that the UUID was wrong has been established. If this is caused by upgrading from Feisty to Gutsy, however, it definitely counts as a bug IMO.

---

### Post by meierfra on 2007-12-21
It could be that  the wrong "kopt=root=UUID" statement was in menu.lst before the kernel upgrade ( and still could be  in there) During kernel upgrades the "kopt=root=UUID " statement is used to determine the "root=UUID" statement in the Ubuntu item.

I checked the O.P previous posts. He ( or she) had some upgrade problems back in June. That might have caused the wrong UUID. Or the OP  did manually    edit the UUID   but did not change the "kopt=root=UUID" statement.

---

### Post by meierfra on 2007-12-21
My main point is: Check that the "kopt=root=UUID" statement is correct. Otherwise you will have the same problem  after the next kernel upgrade.

---

### Post by p_quarles on 2007-12-21
> **meierfra said:**
> My main point is: Check that the "kopt=root=UUID" statement is correct. Otherwise you will have the same problem  after the next kernel upgrade.
OK, I see your point now, and I agree completely.

---

### Post by mneisen on 2007-12-22
> **meierfra said:**
> It could be that  the wrong "kopt=root=UUID" statement was in menu.lst before the kernel upgrade ( and still could be  in there) During kernel upgrades the "kopt=root=UUID " statement is used to determine the "root=UUID" statement in the Ubuntu item.

RIght, I checked that, and surely the kopt line in my menu.lst says

```
# kopt=root=UUID=52bb200c-f962-40a9-9200-bc1ce963210b ro
```

which is wrong and likely to be the source of my problem.

Nevertheless:

> **meierfra said:**
> I checked the O.P previous posts. He ( or she) had some upgrade problems back in June. That might have caused the wrong UUID. Or the OP  did manually    edit the UUID   but did not change the "kopt=root=UUID" statement.

Whooo, data mining in the forums ... :-D

Well, I did have update problems back in June, and I had some in October. So I decided to re-install from scratch. So, this should not be connected to any problems in the past, as my laptop runs a fairly plain-vanilla Gutsy, freshly installed from a ShipIt medium.

Thanks for the advice regarding the kopt-line in menu.lst, I will fix that. But still, I would qualify this as a bug: If the installer writes a wrong vol_id in menu.lst so that a subsequent kernel upgrades fails (or makes the box unbootable), this will be desastrous to most "normal" users.

Thanks for the help, though.

If you need any further information, please post again!

---

### Post by azuth on 2007-12-22
i have laptop boot problem as same..

but it writes

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS process (2456) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Not a directory
init: rc-default process (2457) terminated with status 255

and stops loading..

---

### Post by mneisen on 2007-12-22
Hi azuth,

this:

> **azuth said:**
> i have laptop boot problem as same..

but it writes

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS process (2456) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Not a directory
init: rc-default process (2457) terminated with status 255

and stops loading..

sounds like a different problem since your init-system throws errors at you. It could not do so if you had the same problem, i.e., if your root partition fails to mount.

I would suggest to report this problem in a separate thread in the forum.

Good luck!

---

### Post by meierfra on 2007-12-22
Martin: I just don't  see how the installer could use the wrong UUID for kopt but the correct one in the ubuntu items. Just out of curiosity:  Did you ever  edit menu.lst since you reinstalled?   Did you compare menu.lst with the backup file menu.lst~ ? Any idea where the wrong UUID could come from? (You might look at the results of  "sudo blkid" and "ls /dev/disk/by-uuid")

---

### Post by mneisen on 2007-12-22
> **meierfra said:**
> Just out of curiosity:  Did you ever  edit menu.lst since you reinstalled?

No, I had no reason to do so.

> **meierfra said:**
> Did you compare menu.lst with the backup file menu.lst~ ?

diff gives me the following:

```
mneisen@samsumm:/boot/grub$ diff -rua menu.lst*
--- menu.lst    2007-12-22 00:42:37.000000000 +0100
+++ menu.lst~   2007-12-21 11:24:26.000000000 +0100
@@ -129,13 +129,13 @@

 title          Ubuntu 7.10, kernel 2.6.22-14-generic
 root           (hd0,1)
-kernel         /vmlinuz-2.6.22-14-generic root=UUID=926efc98-7e18-4599-9e26-71cbbdd853c7 ro quiet splash
+kernel         /vmlinuz-2.6.22-14-generic root=UUID=52bb200c-f962-40a9-9200-bc1ce963210b ro quiet splash
 initrd         /initrd.img-2.6.22-14-generic
 quiet

 title          Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
 root           (hd0,1)
-kernel         /vmlinuz-2.6.22-14-generic root=UUID=926efc98-7e18-4599-9e26-71cbbdd853c7 ro single
+kernel         /vmlinuz-2.6.22-14-generic root=UUID=52bb200c-f962-40a9-9200-bc1ce963210b ro single
 initrd         /initrd.img-2.6.22-14-generic

 title          Ubuntu 7.10, memtest86+
```

Looks like it changed the vol_id.

> **meierfra said:**
> Any idea where the wrong UUID could come from? (You might look at the results of  "sudo blkid" and "ls /dev/disk/by-uuid")

No, I have no idea. There is no other partition on the laptop with the vol_id that broke my boot:

```
mneisen@samsumm:/boot/grub$ for i in $(seq 1 4); do echo --- /dev/sda${i} ---; sudo vol_id /dev/sda${i}; done
--- /dev/sda1 ---
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=32A4F634A4F5F9E5
ID_FS_UUID_ENC=32A4F634A4F5F9E5
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
--- /dev/sda2 ---
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=a0ccfb71-65d5-41f9-bc2a-53c3be4d4ddc
ID_FS_UUID_ENC=a0ccfb71-65d5-41f9-bc2a-53c3be4d4ddc
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
--- /dev/sda3 ---
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=8401ad7d-f065-4230-806e-d0d86897f9dd
ID_FS_UUID_ENC=8401ad7d-f065-4230-806e-d0d86897f9dd
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
--- /dev/sda4 ---
ID_FS_USAGE=filesystem
ID_FS_TYPE=xfs
ID_FS_VERSION=
ID_FS_UUID=926efc98-7e18-4599-9e26-71cbbdd853c7
ID_FS_UUID_ENC=926efc98-7e18-4599-9e26-71cbbdd853c7
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
```

The commands you proposed yield:

```
mneisen@samsumm:/boot/grub$ sudo blkid
/dev/sda1: UUID="32A4F634A4F5F9E5" TYPE="ntfs"
/dev/sda2: UUID="a0ccfb71-65d5-41f9-bc2a-53c3be4d4ddc" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda3: TYPE="swap" UUID="8401ad7d-f065-4230-806e-d0d86897f9dd"
/dev/sda4: UUID="926efc98-7e18-4599-9e26-71cbbdd853c7" TYPE="xfs"
```

and

```
mneisen@samsumm:/boot/grub$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-12-22 12:16 32A4F634A4F5F9E5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-12-22 12:16 8401ad7d-f065-4230-806e-d0d86897f9dd -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-12-22 12:16 926efc98-7e18-4599-9e26-71cbbdd853c7 -> ../../sda4
lrwxrwxrwx 1 root root 10 2007-12-22 12:16 a0ccfb71-65d5-41f9-bc2a-53c3be4d4ddc -> ../../sda2
```

I simply cannot figure out where the wrong vol_id came from. I still hope that someone might have an idea.

Thanks again for your help and suggestions!

---

### Post by meierfra on 2007-12-22
> diff gives me the following:.....

Did you run "diff" after you fixed the "kopt=root=UUID" statement in menu.lst?
That would mean that  the kopt statement  in the backup file was correct. 

If this is the  case, I concede. It really seems to be a bug.

---

### Post by mneisen on 2007-12-22
> **meierfra said:**
> Did you run "diff" after you fixed the "kopt=root=UUID" statement in menu.lst?
That would mean that  the kopt statement  in the backup file was correct. 

If this is the  case, I concede. It really seems to be a bug.

Yes, I did run diff *after* fixing the bug, but I did not yet fix the kopt-line. I never edited the menu.lst before, so it really seems that the wrong kopt-line comes from either the installer (most likely) or the kernel update (less likely).

---


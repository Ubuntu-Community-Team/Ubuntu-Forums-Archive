---
title: "Boots into initramfs after &quot;findfs: unable to resolve 'LABEL=writable'&quot;"
date: 2017-02-20
forum: General Help
---

### Post by eriffo on 2017-02-20
I'm running Xubuntu 16.04, kernel 4.4.0-38, on a Lenovo Yoga 700 with an SSD drive.

In a regular boot, it gets stuck for a while like this:

```
[    0.233982] platform MSFT0101:00 failed to claim resource 1
[    0.234071] acpi MSFT0101:00 platform device creatin failed: -16
grep: /proc/device-tree/model: No such file or directory
findfs: unable to resolve 'LABEL=writable'
cannot find 'writable' partition
```

And after a couple of minutes it ends up like this:

```
BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

If I boot in recovery mode it goes verbose, mostly lines about [FONT=Courier New]usb 1-5.1[/FONT], and then:

```
[    2.588963] clocksource: Switched to clocksource tsc
findfs: unable to resolve 'LABEL=writable'
done.
cannot find 'writable' partition

```

Then it goes into BusyBox same as above. I run the [FONT=Courier New]exit[/FONT] command, and get

```

initrd: checking filesystem for writable partition
mount: mounting on /tmpmnt_writable failed: Invalid argument
umount: can't unmount /tmpmnt_writable failed: Invalid argument
ext4
initrd: mounting /dev/sda1
EXT4-fs (sda1): couldn't mount as ext3 due to feature incompatibilities
EXT4-fs (sda1): couldn't mount as ext2 due to feature incompatibilities
EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts:
(null)

```

After a few minutes it goes into a couple of screen apparently trying to complete the boot up. Each screen ends with [FONT=Courier New]A start job is running for dev-disk...writable.device[/FONT] and a 1min 30s countdown, after which it goes to the next screen. In the third and last screen it ends with:

```
[ TIME ] Timed out waiting for device dev-disk-by\x2dlabel-writable.device.
[DEPEND] Dependency failed for /writable.
[DEPEND] Dependency failed for /var/lib/systemd/rfkill.
[DEPEND] Dependency failed for Load/Save RF Kill Switch Status.
```

I'd appreciate any help :-)

---

### Post by kingneutron on 2017-02-21
--Did you make any recent changes to /etc/fstab ?  I recommend booting into a recovery environment (such as systemrescuecd - REF: [https://distrowatch.com/table.php?distribution=systemrescue](https://distrowatch.com/table.php?distribution=systemrescue) ) 

--Once there, issue ' blkid ' and find your root partition (post results of 'blkid' here if you need help)

--Once you find your root partition, in sysrescue:

' mkdir /mnt/tmp '
' mount /dev/sdXX /mnt/tmp '  # substitute XX with your actual drive and partition from blkid

' cd /mnt/tmp '
' cat etc/fstab '  # NOTE this is important not to put a preceding slash in front of etc as we are in your "root"

--Look for something that has LABEL=writable , this is probably an invalid entry / needs to be corrected.

---

### Post by eriffo on 2017-02-22
thanks for the reply!

fstab looks fine. root and swap are there, correctly identified by UUID, not labels. so there's no mention of "writable"

I wonder if it might be something about mbr, uefi, and those things, which I never really understood. BIOS is set to boot in legacy mode, not uefi, if that is relevant.

---

### Post by kingneutron on 2017-02-22
--Kinda stumped then. If you want to save time (basically skip possibly hours/days of head-beating) and get the PC back to functional, I'd backup your files to an external drive and reinstall the OS.  Maybe make sure you have a separate /home partition if you didn't do that the 1st time.

---


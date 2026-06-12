---
title: "Regular fsck and /forcefsck don't work"
date: 2022-06-27
forum: General Help
---

### Post by Paddy Landau on 2022-06-27
[SIZE=3]Background[/SIZE]

I understand that Ubuntu should check the hard drive, by default, every so often when booting.

And, I can create file /forcefsck to force a check when next booting. I trusted this to work, because that file is deleted when I next boot.

Today, after reading something on the web, I decided to check when my drive had last been checked.

I have checked this on two different installations:

[LIST]
[*]Ubuntu 22.04 full-disk installation, UEFI, standard ext4, no encryption
[*]Ubuntu 20.04 full-disk installation, UEFI, standard ext4, LUKS encryption
[/LIST]
[SIZE=3]In both cases:[/SIZE]

I found the date when the filesystem was first created, and the date when last checked. Both of these matched the Ubuntu installation date.
```
sudo dumpe2fs /dev/mapper/vgubuntu-root | grep -F 'Filesystem created'
sudo dumpe2fs /dev/mapper/vgubuntu-root | grep -F 'Last checked'
```

In other words, the file system has never been checked even after using /forcefsck.

I booted the system using a USB drive, and checked the drive manually:
```
sudo fsck -CMf /dev/sda2           # System without encryption
sudo fsck -CMf /dev/vgubuntu/root  # System with encryption
```
On one of the systems, fsck found and fixed some minor warnings.

Now, on both systems, today's date is shown in "Last checked".

[SIZE=3]Question[/SIZE]

Is this failure to run fsck, whether periodically or with /forcefsck, a bug, a "feature", a new restriction, a setting, my misunderstanding, or something else?

---

### Post by TheFu on 2022-06-27
/forcefsck hasn't worked since systemd took over all mounts.  The team has been unwilling to add that huge feature back.  They want us to use grub boot options or Recovery Mode (Advanced Grub menu) to do it. [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Not all file systems can/should be fsck'd.  BTRFS, ZFS, NTFS, exFAT/FAT-whatever don't support it. They have different tools for file system consistency validation. RTFM on each of those.

For ext2/3/4 file systems, we can use tune2fs to set the default number of days or boot or mounts between automatic fsck runs.  I don't remember the default, but I have set it on all my ext4 file systems to be once every 30 or 60 days. I don't recall. Sorry.
Here's the some LVM-LV file systems:
```
$ sudo tune2fs -l /dev/istar-vg/root  |egrep -i Check
Last checked:             Fri Jun 10 14:51:21 2022
Check interval:           2419200 (4 weeks)
Next check after:         Fri Jul  8 14:51:21 2022

$ sudo tune2fs -l /dev/istar-vg/lv_media  |egrep -i Check 
Last checked:             Fri Jun 10 14:51:53 2022
Check interval:           2419200 (4 weeks)
Next check after:         Fri Jul  8 14:51:53 2022

$ sudo tune2fs -l /dev/istar-stuff/lv-tv  |egrep -i Check 
Last checked:             Fri Jun 10 14:51:53 2022
Check interval:           2419200 (4 weeks)
Next check after:         Fri Jul  8 14:51:53 2022

```

We don't have to use the defaults. Humans are smarter than just choosing default settings.

---

### Post by sudodus on 2022-06-27
+1: We don't have to use the defaults.

I set 30 days interval between checks with
```

sudo tune2fs -i 30 /dev/sdxn

```
on the drives in my main computer. Things happen that make me check/fix the file systems manually too, but only a few times per year.

---

### Post by TheFu on 2022-06-27
The tune2fs setting won't start an fsck in the middle of any work, it is only at boot time when this is checked.  So, about once a month, a reboot will cause the specific file system to be fsck'd.  If there are lots of disks, it might be smart to stagger the reboot period a week or two apart to avoid having 10 file systems running fsck at the same reboot.  Because I reboot about once every 2-3 weeks, it is harder for me to prevent all the fsck tasks from bunching up.  That's where the 6th field in the fstab can help a bit ... or not using the fstab to mount all the extra storage (I use autofs) for a bit more control.

---

### Post by Paddy Landau on 2022-06-27
> **TheFu said:**
> /forcefsck hasn't worked since systemd took over all mounts.  The team has been unwilling to add that huge feature back.
Oh. That explains it! Thank you.
> **TheFu said:**
> We don't have to use the defaults. Humans are smarter than just choosing default settings.
Sometimes, yes! In this case, the default is zero, so definitely.
> **sudodus said:**
> I set 30 days interval…
Thanks for that. I see that you can set a time (-i [time]) or the number of mounts (-c [count]).
> **sudodus said:**
> Things happen that make me check/fix the file systems manually too, but only a few times per year.
How do you check it manually? I booted from a USB drive. Is there an easier way?
> **TheFu said:**
> … it might be smart to stagger the reboot period…
Indeed. This is mentioned in the manual. I have three partitions on my main system: EFI, /boot and root. I don't know how to set the EFI partition (FAT32), though I imagine that it's not problematic, being rarely changed.

---

### Post by sudodus on 2022-06-27
To check manually I boot into another system. In this case I have other systems installed internally, but in the general case it would be from a USB drive.

---

### Post by TheFu on 2022-06-27
> **Paddy Landau said:**
> How do you check it manually? I booted from a USB drive. Is there an easier way?


Easier is subjective.  Already answered in post #2 above.

---

### Post by Paddy Landau on 2022-06-27
> **TheFu said:**
> Already answered in post #2 above.
Are you referring to Recovery Mode? That didn't work for me, because the drive was mounted.

---

### Post by TheFu on 2022-06-27
> **Paddy Landau said:**
> Are you referring to Recovery Mode? That didn't work for me, because the drive was mounted.

Well crap.  That's a bug.  I've used previously and it worked.  I'm seeing 3 bugs for it being mounted rw.   

I remember there was an option to fsck all file systems on the system and I've used it, just not recently.
Looks like we all need to keep that Try Ubuntu flash drive handy still.

---

### Post by #&amp;thj^% on 2022-06-27
> **sudodus said:**
> To check manually I boot into another system. In this case **_I have other systems installed internally,_** but in the general case it would be from a USB drive.

I've found this to be the Best chance for a successful fsck.
Not to forget nothing replaces a good back-up strategy.

---

### Post by Paddy Landau on 2022-06-27
> **TheFu said:**
> That's a bug.
I don't think so. Checking a mounted drive can lead to problems. That's why I always use option -M with fsck.

---

### Post by TheFu on 2022-06-27
> **Paddy Landau said:**
> I don't think so. Checking a mounted drive can lead to problems. That's why I always use option -M with fsck.

It is easy to boot into a RAM-only Linux environment, then no storage would be mounted.  That's the bug.

---

### Post by Paddy Landau on 2022-06-28
> **TheFu said:**
> It is easy to boot into a RAM-only Linux environment, then no storage would be mounted.  That's the bug.
So, to implement this, should there be an option in Grub to do this?

---

### Post by TheFu on 2022-06-28
> **Paddy Landau said:**
> So, to implement this, should there be an option in Grub to do this?

Grub already has a method. The boot command can be edited with the obtuse systemd-fsck option (which I don't have memorized) either on the grub screen or in the   /etc/grub.d/ files.  These somehow force:
```
systemd-fsck (8)     - File system checker logic
systemd-fsck-root.service (8) - File system checker logic
systemd-fsck@.service (8) - File system checker logic
systemd-fsckd (8)    - File system check progress reporting
systemd-fsckd.service (8) - File system check progress reporting
systemd-fsckd.socket (8) - File system check progress reporting
```
one of those to be used.

[https://askubuntu.com/questions/1359037/how-to-run-fsck-on-the-root-partion-from-the-grub-menu](https://askubuntu.com/questions/1359037/how-to-run-fsck-on-the-root-partion-from-the-grub-menu) says to edit the boot command adding, *fsck.mode=force* to the boot options.  The *sudo tune2fs -c 1 /dev/path/to/filesystem/device* method could be used as well.

The problem with the recovery console is that the "Run fsck on all disks" isn't loaded in RAM only and has left any storage mounted. No storage should be mounted.

---


---
title: "Welcome to Emergency Mode"
date: 2017-09-25
forum: General Help
---

### Post by Rick St. George on 2017-09-25
I had added another HD to pull info off it. Would not mount due to Windows Lock. Suggested to boot in Read ONLY mode, which I did. But had to add to FSTAB the UUID. Afterwards, shutdown, and removed it.

Upon Boot-up, I get "Welcome to Emergency Mode". Can't get my computer to boot. What can I do now?

Thanks for any and all help.

Rick

---

### Post by Bashing-om on 2017-09-25
Rick St. George; Hello;

Let's say that the fstab file is now inconsistent.
Let's take a gander at what is now the installed fstab.
Boot up a liveDVD(USB) to "try ubuntu" mode.
Activate a terminal ( ctl+alt+t ) :
Know the partitioning to know the target location .
```

sudo parted -l

```
Now suppose that the target as shown by parted is sda1 ( ext4 - file system ; boot - flags ) such that we know it must contain the fstab file ,

Now next is to mount that partition from the live environment:
Still supposing that sda1 is the target .
then:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda1 /mnt/looksee

```

Now we have that gander at the file:
```

cat /mnt/looksee/etc/fstab

```
Now compare the UUID's of the fstab file to what the system says is the correct UUIDs
```

sudo blkid -c /dev/null

```
( this will give all UUIDs in use by partitions / drives etc. The "-c /dev/null" forces blkid to poll the hardware for the UUID so as not take it from an OS cached file.)

If you have any reservations as to what you read and see from blkid as the fstab file ; post the results for our examination .
 
As we are done here presently ; we MUST UN-mount that we mounted  !
-not doing so can leave the file system in a bad bad state !
```

sudo umount /mnt/looksee

```

[INDENT]ain't nothing bit a thing
[INDENT][INDENT]but needs to be done
[/INDENT][/INDENT][/INDENT]

---

### Post by Rick St. George on 2017-10-04
Simply # commented out that line I added, until next time I need it to copy files off that HD.
Afterward, I will simply remove that line, and will also remove that HD before rebooting.

Thanks for your comments "Bashing-Om".
Peace,
):P
Rick

---

### Post by Bashing-om on 2017-10-04
Rick St. George; Hey;

While your procedure is certainly doable, it is a bit clumsy .

A mount option in fstab might be the more elegant:
> 
noauto - The filesystem will NOT be automatically mounted at startup, or when mount passed -a. You must explicitly mount the filesystem.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

But do note, I too only mount my data drives as " on demand" explicitly from terminal .

[INDENT]'buntu
[INDENT][INDENT][INDENT]many paths to an end[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2017-10-04
If you're talking about an NTFS volume, see this: [https://www.howtogeek.com/236807/how-to-mount-your-windows-10-or-8-system-drive-on-linux/](https://www.howtogeek.com/236807/how-to-mount-your-windows-10-or-8-system-drive-on-linux/)
In other words, you shouldn't need to add it to fstab or force-mount it read only. If you use the drive primarily in a Windows-only system, I'm guessing you don't want to disable fast boot completely, but rather, make sure you do this before you pull the drive:
> To prevent Windows from (hibernating) and force it to perform a full shut down, you can press and hold the Shift key while you click the &#8220;Shut down&#8221; option in Windows. Windows will perform a full shut down when you also hold the Shift button.

---


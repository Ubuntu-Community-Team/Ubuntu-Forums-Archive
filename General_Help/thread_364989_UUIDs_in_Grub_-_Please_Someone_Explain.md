---
title: "UUIDs in Grub - Please Someone Explain"
date: 2007-02-18
forum: General Help
---

### Post by rbil49 on 2007-02-18
I just updated my system from Dapper to Edgy. Looks like the update went alright. Still a few things not working properly but I'll look into seeing if I can fix them.

What I noticed of course is that now Ubuntu is using UUIDs instead of /dev/hdX to point to hard drive partitions in fstab. I guess I can live with that. But I don't really like it. It's so Microsoftish using long Classids instead of something that makes far more sense and is human readable which has been a tradition with GNU/Linux.

But why in the world would the developers decide to do the same thing in Grub??? Grub is so important to booting up a working system. Now imagine this scenario which is a VERY common practice. Users decide to clone their working hard drive to other hard drives either to quickly update other boxes or simply to replace a smaller hard drive with a larger one. Third-party software like Acronis True Image make it easy to create clones like this for backup purposes.

Now what will happen when this clone drive gets booted and the UUID no longer matches this new drive? Will Grub even boot or will one be left with a real broken system? Even if the new hard drive could boot, would the use of UUIDs to describe the main internal drives in fstab also create big problems? 

I'd really like to hear from whoever decided to move to UUIDs to explain why they'd even think of using them in Grub's menu.lst and for non-removable drives? None of this makes any sense to me and seriously imperils the system. 

Thanks

Cheers.

---

### Post by dcstar on 2007-02-18
> **rbil49 said:**
> I just updated my system from Dapper to Edgy. Looks like the update went alright. Still a few things not working properly but I'll look into seeing if I can fix them.

What I noticed of course is that now Ubuntu is using UUIDs instead of /dev/hdX to point to hard drive partitions in fstab. I guess I can live with that. But I don't really like it. It's so Microsoftish using long Classids instead of something that makes far more sense and is human readable which has been a tradition with GNU/Linux.

But why in the world would the developers decide to do the same thing in Grub??? Grub is so important to booting up a working system. Now imagine this scenario which is a VERY common practice. Users decide to clone their working hard drive to other hard drives either to quickly update other boxes or simply to replace a smaller hard drive with a larger one. Third-party software like Acronis True Image make it easy to create clones like this for backup purposes.

Now what will happen when this clone drive gets booted and the UUID no longer matches this new drive? Will Grub even boot or will one be left with a real broken system? Even if the new hard drive could boot, would the use of UUIDs to describe the main internal drives in fstab also create big problems? 

I'd really like to hear from whoever decided to move to UUIDs to explain why they'd even think of using them in Grub's menu.lst and for non-removable drives? None of this makes any sense to me and seriously imperils the system. 

Thanks

Cheers.

My 6.10 Grub menu.lst does not use UUIDs, but my fstab does.

Perhaps you could post your file so we can see exactly what is happening?

---

### Post by rbil49 on 2007-02-18
Sure, here is the relevant part of my menu.lst ...

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro single
initrd		/boot/initrd.img-2.6.17-11-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Patrick K on 2007-02-19
Mine doesn't use UUID numbers either (fstab does since the upgrade). If you want to see what devices have what UUID number, open Device Manager and look on the advanced page. It's the last entry.

---

### Post by dcstar on 2007-02-19
> **rbil49 said:**
> Sure, here is the relevant part of my menu.lst ...

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=3ead8fbe-d3c0-45c6-9924-94e06e2654d1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot
.........

### END DEBIAN AUTOMAGIC KERNELS LIST

Wow, my Grub files has are the standard "/dev/hda..." stuff - and that was from a fresh Edgy install.

I know that UUIDs are useful for things like removable drives (so the correct drive is used), but in a Grub menu they seem to over-complicate things - especially for your fixed drives.

There could well be a good reason for using them in Grub, but I don't know of it.

---

### Post by rbil49 on 2007-02-19
Good to know that UUIDs aren't required. I did an update from Dapper and that is what I ended up with in menu.lst. I'm going to manually change them to /dev and remove those stupid UUIDs.

I guess I'll see what happens when a new kernel comes along and how it will be addressed in Grub.

Know of any reason to not get rid of UUIDs in fstab for fixed disks? I really don't like them and think that it'll break things should the disk be cloned.

Cheers.

---

### Post by dcstar on 2007-02-19
> **rbil49 said:**
> Good to know that UUIDs aren't required. I did an update from Dapper and that is what I ended up with in menu.lst. I'm going to manually change them to /dev and remove those stupid UUIDs.

I guess I'll see what happens when a new kernel comes along and how it will be addressed in Grub.

Know of any reason to not get rid of UUIDs in fstab for fixed disks? I really don't like them and think that it'll break things should the disk be cloned.

Cheers.

You can reference partitions by multiple means now - they all have various advantages and disadvantages.

For instance, I give the partitions on my USB sticks labels, so they are always mounted with these rather than /dev/sda-whatever - that means the backups on my financial software always go to the right device.

I probably could use UUIDs to do this (and eliminate the risk of multiple devices with the same label), but the labels are much easier for me to comprehend!

If you install the pysdm package, it actually uses the "standard" /dev identifiers when it writes entries to your fstab file, so it it's good enough for a system utility to do this, it should be ok for you to do it as well!

---

### Post by RAOF on 2007-02-19
The UUID's are there for the use-cases "What happens if I add another hard-drive, and my /dev/hda stuff gets renamed" and "The 2.6.20 kernel has *everything* on /dev/sd?, what happens to my /dev/hda1 GRUB item".

You can check these things out - check out /dev/by-uuid and the like.

---


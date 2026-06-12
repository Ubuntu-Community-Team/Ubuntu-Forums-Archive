---
title: "kernel panic caused by screwing with the swap partition"
date: 2006-09-25
forum: General Help
---

### Post by rjs on 2006-09-25
G'day all,

I set up a friend's computer to dual boot (win XP and kubuntu 6.06
i386) and everything went all peachy untill...

what we planned to do was have a ntfs windows partition a linux ext3
partition and a shared FAT32 documents partition (since ntfs under
linux still isn't quite up to scratch). It is a Dell laptop and dell
has a tiny FAT16 partition that it has some random files in (i don't
quite know what they do so i didn't want to touch them) and then linux
needs a linux-swap so that is 5 partitions all up. When i was setting
it up i hadn't used qtparted before and couldn't quite work out how to
create extended partitions so we had the dell partition, the windows
partition, the linux partition and the linux-swap partition and a
whole heap of free space (and we thought we would work out how to
create an extended FAT32 partition later).

So just now i deleated the linux-swap partition (assuming since it was
just swap it wouldn't matter) and turned that into an extended
partition with linux-swap as the first logical partition on it and
then the rest being the FAT32 logical partition.

Windows can now read/write the FAT32 partition just fine (as
expected), but poor old linux; well it can't boot anymore (as probably
should have been expected but wasn't). It gets to the "mounting root
filesystem" part of the boot process then just hangs. In the "recovery
mode" it gives the following when trying to boot:

<blah blah blah />
Begin: Running  /scripts/local-premount...
[17179573.152000] Attempting manual resume
[17179573.152000] attempt to access beyond end of device
[17179573.152000] sda4: rw=16, want=8, limit=2
[17179573.152000] Kernel panic - not syncing: I/O error reading memory image
[17179573.152000]

note: sda4 is the name of what used to be linux-swap and got turned
into an extended partition

anyways, i updated fstab (by mounting the linux partition with a liveCD) with the new location of the linux-swap partition (sda6) and tried again. Same result. I also adeed a noresume instruction to grub, and that didn't help either. Sooo... now i'm stumped. Anyone got any other ideas (including possible stupid mistakes i might have made with the last to ideas)?

paz,
-rjs.

---

### Post by jdong on 2006-09-25
You need to reformat the swap partition using the mkswap command and a livecd. Be careful to specify the right block device, as it only takes a few fractions of a second for mkswap to destroy the existing partition :)

---

### Post by rjs on 2006-09-25
Sorry, not to doubt what you say, i just want to clarify. Why would the swap partition need formatting if it has just been created by qtparted. Surely qtparted would have formatted it when it created the new swap partition (or am i missing something here?).

paz,
-rjs.

---

### Post by jdong on 2006-09-25
Oh sorry, misread your post.... it seems like the init scripts are trying to resume from a now nonexistent /dev/sda4 device.

Try booting once with "resume=/dev/null"

---

### Post by rjs on 2006-09-25
Thanks, i will try that.

paz,
-rjs.

---

### Post by hearnden on 2006-09-25
If the problem keeps occurring unless you override your boot line with resume=..., then perhaps your kernel image has the wrong resume device built in to it.  I noticed that mine was pointing to the wrong device right after doing some kernel upgrades, and boy did it take me a long time to find out what was going on (not booting from kernel panics made that kind of hard)!  Have a look in /etc/mkinitrd/mkinitrd.conf for a line "RESUME=...", and, if it exists, make sure it is set to your swap partition.  Also look for this file: /etc/mkinitramfs/conf.d/resume, and see if it has one line of the same form "RESUME=...", and make sure, if it exists, that it is set to your swap partition.

If neither of those files contain those lines, or they were already pointing to the right place, then don't worry.  But if you changed either of the above, you need to rebuild your kernel image with:

```

$ sudo dpkg-reconfigure linux-image-$(uname -r)

```

---

### Post by rjs on 2006-09-26
Ok,

I might be missing something here, but it says that resume is not a recognised command. Also when i exit back to the grub menu and then press e again it hasn't saved the changes i just made but if i press b right after i make the changes it tries to boot (and then tells me that it doesn't understand resume=/dev/sda5). It also says that it doesn't understand noresume (which someone else suggested at my local lug).

Looking at the grub documentation i can't find a resume or noresume command (or any similar command).

paz,
-rjs.

---

### Post by jdong on 2006-09-26
noresume/resume=? is not a grub command. It's a kernel argument that you put at the end of the line that starts with "kernel /"

---

### Post by hearnden on 2006-09-26
They're not commands, they are options you pass in the kernel line:

```

kernel          /vmlinuz-2.6.15-27-686 root=/dev/sda5 resume=/dev/sda2 ro quiet splash 

```

My Ubuntu filesystem is /dev/sda5, and my swap partition is /dev/sda2.  You'll want resume=/dev/sda6, but I don't know what your root Ubuntu partition is.

But just to address your partitioning motivations, there are a number or tools (e.g. [http://www.fs-driver.org](http://www.fs-driver.org)) that will let you use Linux partitions in Windows, so if your only motivation for the FAT32 partition is to share files, then it is unnecessary.  If that brings your total partitions down to 4, then you may not need any extended partitions.

---


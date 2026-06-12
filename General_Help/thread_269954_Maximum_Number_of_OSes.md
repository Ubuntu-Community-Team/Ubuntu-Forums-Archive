---
title: "Maximum Number of OSes?"
date: 2006-10-02
forum: General Help
---

### Post by tonyr1988 on 2006-10-02
I became curious about something today...

Is there a maximum number of operating systems you can install on a computer (assuming that disk space isn't an issue)? I would assume no, but then again,  I've heard of people quad-booting their system and getting "ooh"s and "aah"s from it.

I thought of this when I saw a YouTube video of a quad-boot system. They had Ubuntu, WinXP, Vista, and a MacOSX (perfectly illegal :P). The thing I noticed that was weird is that, upon boot, it did this:

Booted GRUB. GRUB showed: Ubuntu (a few entries, by default) and something like "Vista Boot Menu".
When he clicked the Vista Boot Menu, then it showed WinXP, Vista, and Mac OSX.

Why didn't he just throw them all into GRUB?

Just curious about some of the realistic limitations of having multiple OSes.

Thanks in advance,
Tony R.

---

### Post by Ramses de Norre on 2006-10-02
> **tonyr1988 said:**
> The thing I noticed that was weird is that, upon boot, it did this:

Booted GRUB. GRUB showed: Ubuntu (a few entries, by default) and something like "Vista Boot Menu".
When he clicked the Vista Boot Menu, then it showed WinXP, Vista, and Mac OSX.

Why didn't he just throw them all into GRUB?
That's called chainloading, you use grub to load another boot manager. I don't like it and I keep everything in one grub menu, but the advantage of chainloading is that every OS can have it's own menu.lst that is automaticaly changed on kernel upgrades. I need to do this myself for every OS that I added to my ubuntu grub.

And I'm currently tribooting between ubuntu, zenwalk and XP but I've never tried more then three yet.

---

### Post by GStubbs43 on 2006-10-02
Well, usually Hard Rives can only hhave 4 partions, so about 3 + swap... I think.

---

### Post by wenzlicker on 2006-10-02
[http://www.justlinux.com/forum/showthread.php?threadid=143973]("http://www.justlinux.com/forum/showthread.php?threadid=143973")

This is a link to 100 plus OS's. I don't think there is a limit, as long as you can have the partitions.

---

### Post by Ramses de Norre on 2006-10-02
4 primaries, but you can use extendeds too and many people have more than one hard drive these days so you can definitely have more then 4 OS's.
(I have 7 partitions in my machine for the moment..)

---

### Post by tonyr1988 on 2006-10-02
So you can run OSes out of extended partitions?

And GRUB doesn't have a problem loading any type of OS from any partition? GRUB just sends you to the partition you pick, right?

EDIT: Just read the JustLinux post - wow, that's amazing. So GRUB can boot pretty much anything. Does it just point you to the right place, or am I wrong about that? (I'm guessing on it)

---

### Post by bigaltx on 2006-10-02
There's a maximum number of partitions a hard drive can manage. I forget what the exact number is, but it's way up there, like 50 or 60 partitions. So in theory you can install a bunch of OSs on a hard drive. The rub comes if you want more than 3 Windows systems, Windows systems are'nt real happy when you install them on an extended partition. Unix based systems on the other hand are don't complain at all when installed on an extended partition, so with enough space you can install alot of Unix based systems on a single drive. As long as the grub menu list or grub.conf is right they shoud boot. I've had 6 OSs on a single drive, and did'nt have any problems.

---

### Post by meatface on 2006-10-03
I remember watching 'The Screen Savers' on TechTV a few years back and they had a guy on there that had something like 28 os's on his box. And yes they all booted, but I believe that he was using a windows based boot manager, like boot magic maybe. Anyway it was pretty cool. All I really know is that the more you add the trickier it gets. I have had three os's at once with no trouble.

Cheers

Meatface

---

### Post by Rhapsody on 2006-10-03
If I'm thinking right, the maximum number of partitions a hard drive can have is 64, including all types (primary, extended, and logical). This means the maximum amount of usable partitions (an extended partition can't be used by itself, it can only contain logical partitions) is 63, making that the maximum number of OSes you can possibly install on one drive at once.

Of course, you can also have more than one hard drive, and I don't think most OSes care which drive they're on. Using Serial Attached SCSI allows for a total of 16,256 drives each with a maximum of 63 usable partitions on it.

This leaves you with a theoretical maximum of 1,024,128 OSes with no swap partitions, or 512,064 with an additional swap partition for each.

Of course your boot loader menu would become unmanagable well before you hit either of these limits, but there they are anyway.

---

### Post by Ramses de Norre on 2006-10-03
We'll have to wait for the first guy with 1,024,128 OSes to post a video of it on the internet =)

(And one swap partition is enough for all partitions, they can all use the same.)

---

### Post by Rhapsody on 2006-10-03
> **Ramses de Norre said:**
> We'll have to wait for the first guy with 1,024,128 OSes to post a video of it on the internet =)

(And one swap partition is enough for all partitions, they can all use the same.)
Well there we go then. Also, if you can afford 16,256 hard drives, you can probably afford enough RAM to not strictly need a swap partition.

---


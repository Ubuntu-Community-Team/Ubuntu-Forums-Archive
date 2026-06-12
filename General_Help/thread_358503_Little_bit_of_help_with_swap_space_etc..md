---
title: "Little bit of help with swap space etc."
date: 2007-02-10
forum: General Help
---

### Post by HybridGhost on 2007-02-10
Hey,

My name is Jory and it's my first time on these forums, I'm not entirely new to this but this time I want to make sure I do it right :D

I have 2x 150G HD's

How I'm thinking of setting this up is...

Drive 1 - Enough space to fit Windows OS (NTFS) ; Ubuntu Swapspace (Ext2) - (What else do I need?)

Drive 2 - Enough space for Ubuntu OS (Ext2) ; Windows Swapspace(NTFS) - (What else do I need?)

Main reason is for speed purposes, how large should I have the OS spaces?  Should there be extra space ect? Is that all I need?  I'm planning on using wine yet again as I only use Windows when 100% Necessary.

Also should I use Ext2 or Ext3 and what's the real difference?

Thanks for the input and I hope I explained this well enough for someone to be able to help me, I also hope that I posted this in the write forum :)

Regards,

---

### Post by Stephen Howard on 2007-02-11
On drive 2 I'd probably add the following:

/home[INDENT]I've found its best to keep /home on its own partition so that you can reinstall linux from scratch without losing your personal settings ie gnome/kde settings etc.[/INDENT]

/usr/local[INDENT]if you have programs that are not part of a distribution (eg commercial programs such as linux games or even an mp3 collection), its best to keep them on a separate partition (I call mine /usr/local) for the same reason as the /home partition.[/INDENT]

/tmp[indent]especially if you want to encrypt it.[/indent]

---

### Post by Stephen Howard on 2007-02-11
The only significant difference between ext2 and ext3 is that ext3 has journalling bolted on to it.  I wouldn't bother with it.

---

### Post by Stephen Howard on 2007-02-11
As for partition sizes, a rule of thumb for swap space is that it should be about the same size as the RAM on the machine.  It really depends on the use to which you want to put your PC.

PS:  try and position the swap partition on the outer tracks of the hd - apparently this is better for access speed.  Alternatively, if you have a partition that you know will be busy, then place the swap partition next to it (on the outer side).

I have no idea how much partition space windows wants.

---

### Post by HybridGhost on 2007-02-11
Thanks for the input guys, I'll see what I can do from here :)

Regards,

---

### Post by HybridGhost on 2007-02-11
Anyone else have any input here?  Swap space as much as the ram, I have four gigs but is that all I need is the OS space and swapspace?

Regards,

---

### Post by Stephen Howard on 2007-02-11
That's extreme ram, and the swap rule of thumb breaks down at such large amounts.  I'd set it at 256mb and then do some testing.  The idea is that you run a whole bunch of ram intensive programs to see if your heaviest usage even fills your ram.  

Test by opening up a terminal and running: [FONT="Fixedsys"]free -ms 5[/FONT]   Then start up the ram intensive programs on the desktop until the free command is reporting negligible unused ram left.  If your processor hasn't ground to a halt and is still hungry for more, then look at increasing swap.

PS: I think that Linux only takes a swap space of 2gb.

---

### Post by Stephen Howard on 2007-02-11
You'll also want to make sure you've got high memory support compiled into your kernel.  If its not, then linux will only use 1gb (or less) of the available ram.

---

### Post by ESPOiG on 2007-02-11
i have mine set up sorta like this, but ill adjust it for your hdds, i use windows for games only and if it stuffs up i have it set up for a specific reason

hdd 1
part1(ntfs) - windows root - for main windows
part2(ntfs) - windows install - for installing programs/games for backup so you dont lose save games etc when you have to install windows again
part3(fat32) - windows share - sharing - sharing files between windows and linux

hdd2
part1(ext2/3) - / - root
part2(ext2/3) - /home - home
part3(swap) - swap

it works great for me

---

### Post by ESPOiG on 2007-02-11
> **Stephen Howard said:**
> You'll also want to make sure you've got high memory support compiled into your kernel.  If its not, then linux will only use 1gb (or less) of the available ram.

whats high memory support and how do u get it :D, this is the first i have heard of it

---

### Post by Stephen Howard on 2007-02-11
> whats high memory support and how do u get it , this is the first i have heard of it

Unless you are into rolling your own kernel, its best to just run the SMP kernel from the repositories - it has highmem support compiled into it.

Without highmem, the kernel won't use memory above ~900mb.

From the console, type:  [FONT="Fixedsys"]dmesg | less[/FONT]

The first page will have a field headed HIGHMEM & LOWMEM.  There'll also be a warning there if you actually have enough ram to use HIGHMEM but your kernel doesn't have the option compiled into it.

Note also that highmem support is just a fraction slower than non-highmem, but the extra ram makes it all worthwhile because the CPU will rarely need to use the v.slow harddrive as swap space.

---


---
title: "Did my system just die?"
date: 2007-04-11
forum: General Help
---

### Post by bg1256 on 2007-04-11
Today when I turned on my pc, I had something happen that has yet to happen to me over the past six months. For the record, I'm booting into Kubuntu Edgy kernel 2.6.17-11-generic.

It started booting normally, then about halfway through, it suddenly changed to a text display.

At first, I thought it was the normal disk check .... this disk has been mounted 30 times ... force checked .. .etc, etc.

However, it was most definitely not this.

Here is what showed up:

```
*Activating Swap...                         [ ok ]
*Checking root file system ... 
sck 1.39 (29-May-2006
dev/sda3: clean, 302388/12107776 files, 6377113124185857 blocks
                                                                 [ ok ]

*Checking file systems ... 
sck 1.39 (29-May-2006)
_
```

And that's it.  It hung there for quite some time with nothing happening... just the blinking "_" .

I repeat, this did not appear to be the normal disk check, and the problem is it froze there.

I also attempted to boot into recovery mode, and I got to the same place, and it froze.

The only change I can remember making to my system yesterday was installing wine to play on pokerstars.net.

I let it run for about 10-15 minutes before I had to shut it down, since I'm going to be gone for the next eight hours or so...

If anyone knows what this is or what I need to do about it, please let me know.

Thanks!

---

### Post by smbm on 2007-04-11
Can you boot from a live cd and mount/access your hard drive(s)?

This could determine whether you have a broken hard disk or broken software.

---

### Post by bg1256 on 2007-04-11
That was my first thought.  This computer is only eight months old, but I assume anything is possible.

I will try booting into Windows, as it's a dual-boot machine.  That will probably be simpler than the Live CD.

---

### Post by bg1256 on 2007-04-11
Windows boots normally, so the HD is not the problem.

Since recovery mode doesn't get me anywhere, I'm assuming my OS just crashed?  And I guess it's safe to assume a fresh install is in order?

The only thing left I can try is booting from an older kernel...

---

### Post by bg1256 on 2007-04-11
Well, here's a major problem.

I just reformatted my root partition, and guess what?  I got stuck at the same screen.

I'm a little concerned now.

edit:

A more full explanation --

I booted into Windows, no problem.  It detected my FAT32 partition, and the data on it appeared to be safe.  The FAT32 partition is where I keep most data, so I wasn't concerned.

I thought, I'll just do a quick format of my root partition and start from scratch.  However, that did not work.  I'm right back where I started.

Is it even possible for part of my hard disc to be corrupted and not all of it?

---

### Post by bg1256 on 2007-04-11
Another update:

I have a SuSE 10.2 DVD, so I went ahead and installed that, just to see what happened.

That installed fine, and I was able to boot from my HD.

Then, I reformatted again with Kubuntu 6.10, thinking it would help, but it didn't.

I am still stuck at the same text screen.

I'm curious: is there a program I could run, perhaps from within Windows, that would scan my entire disc (ext3 included) and tell me if it's a hardware problem?

---


---
title: "[SOLVED] problem burning files to DVD; program says I need DVD+R DL"
date: 2008-01-18
forum: General Help
---

### Post by goulo on 2008-01-18
System/Computer shows I have a CD-RW/DVD±RW Drive.  That means I should be able to write to a DVD+R disc, right?  I put a blank DVD+R into the drive and Ubuntu 7.10 64bit correctly recognizes it as such.  But when trying to write the files (with Nautilus 2.20.0) I get an error when I say "Write to disc":

Please replace the disc in the drive with a supported disc with at least 4.7 GiB free.  The following disc types are supported:
DVD+R DL

Why does the program say I need to use a DVD+R DL disc and refuse to use a DVD+R disc?  This is my first experience trying to burn files onto a DVD.  Am I misunderstanding something, or is there some setting/preference I'm not finding?  Thanks for any help.

---

### Post by lswest on 2008-01-18
DL means dual layer, but that isn't necessary (has storage up to, i believe, 9.4GB) but have you installed a burner program? because if you do you can test if burning works to a DVD, otherwise, well, i'd have to assume the drive just doesnt support it.

---

### Post by heindsight on 2008-01-18
I suspect what's happening is that the files you are trying to burn don't fit onto a normal DVD+R. The DVD+R probably claims to have 4.7GB capacity, but that is 4.7*1000^3 bytes which is actually only approximately 4.3GB (4.3*1024^3).

Nautilus is asking you to insert a DVD+R DL disk, because that's the smallest-capacity disk onto which it can fit your files.

---

### Post by goulo on 2008-01-18
Hi, thanks for the quick reply! The only thing I've installed related to DVDs is:
sudo apt-get install ubuntu-restricted-extras
 as per [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Ok, I found [https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning) and tried the command line (with growisofs) instead of GUI method and was able to write the DVD fine.  So apparently the Nautilus GUI is just lamely broken about DVD burning for some reason.  Grr.  (Can other people burn DVDs fine while browsing with Nautilus?)

But I got the DVD burned fine via the command line, so all's well that ends well... :)

Edit: I think the second comment was right:
>I suspect what's happening is that the files you are trying to burn don't fit onto a normal DVD+R. The DVD+R probably claims to have 4.7GB capacity, but that is 4.7*1000^3 bytes which is actually only approximately 4.3GB (4.3*1024^3).

>Nautilus is asking you to insert a DVD+R DL disk, because that's the smallest-capacity disk onto which it can fit your files.

I did find that the files were too large and I had to remove a few before it would fit.  So Nautilus was giving a rather unclear error message.  Thanks!!!

---

### Post by LowSky on 2008-01-18
> **goulo said:**
> I did find that the files were too large and I had to remove a few before it would fit.  So Nautilus was giving a rather unclear error message.  Thanks!!!

What was unclear it said you needed a bigger disk... BTW mark the thread as solved

---

### Post by goulo on 2008-01-18
> **LowSky said:**
> What was unclear it said you needed a bigger disk... BTW mark the thread as solved

The unclearness was that it WASN'T telling me I needed a bigger disk; it was telling me I needed a different disk format.  It had in fact told me that my disk DID have enough space due to the "ambiguity of 1000 vs 1024" problem.

Marked as solved; thanks for pointing that out.

---

### Post by zorkerz on 2008-01-25
Yes I came across the same problem. Dame annoying that they label DVD as 4.7gb when its only 4.3. I still can't explaine the Gibt (gb) and GiB difference.
I posted a bug on launchpad [https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/185821](https://bugs.launchpad.net/ubuntu/+source/nautilus-cd-burner/+bug/185821)
Its of minute importance but it has sure made a few of us stumble.
cheers

---


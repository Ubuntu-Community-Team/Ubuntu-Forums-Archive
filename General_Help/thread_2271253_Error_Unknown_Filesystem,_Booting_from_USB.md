---
title: "Error: Unknown Filesystem, Booting from USB"
date: 2015-03-28
forum: General Help
---

### Post by solluxptor1 on 2015-03-28
Hello, I sadly had to make this thread, as none of the threads with the same issue managed to fix my issue.

Background: My computer, for about a year now, has been slightly iffy on the software side, because Windows became corrupted through a virus. In the past I have been able to use Ubuntu until I can get it fixed, but this time, my computer won't even detect any operating systems either on the hard drives I have or on the USB I have previously gotten a hot fix using, after a windows update tried updating, which I was fearing because whenever Windows has an 'urgent update,' it's guaranteed to break something on my computer. 

Whenever I try booting up my operating system, whether Windows on the hard drive, or Ubuntu desktop or even Ubuntu server (I tried re downloading both, twice) on my USB, I get:

Boot Error


Error: unknown filesystem
entering rescue mode...
grub_rescue>

I tried doing 

grub_rescue> set boot(hd2, msdos5) //Which is where my Linux .iso is

but it tells me:

error: not an assignment

I have tried telling it to boot from both of my hard drives, and my USB, but it won't work, and from rescue mode, it says none of my hard drives, or (hdX,msdosX), systems are known filesystems.

Also, an odd occurrence, when I started using my Raspberry Pi for the recovery process, it eventually also started failing to boot with unknown filesystems, although I acknowledge that's an error for another time, perhaps it may be related or known in some way. As of right now, even the Mac system I'm using to type this says only the files I put on my usb are on it, so I don't think I some how implanted a virus I got from my desktop and put it on my Pi.

My computer only has an 8GB USB for external hard drives, because, sadly, my computer is incompatible with a disk drive, making Windows recovery from disk impossible.

---

### Post by sandyd on 2015-03-29
Have you tried creating a new USB from Mac?

See [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)

May also work using Unetbootin, but I've never tried.

---

### Post by solluxptor1 on 2015-03-29
I just tried that, but, since the Mac isn't my computer, i wasn't allowed to do one of the final steps in sudo, however, I managed to get my Pi working again after formatting and reinstalling its operating system, so I suppose the next step in solving this is, if anyone knows how to make a bootable Ubuntu USB, using only Raspbian? If this is something better asked on a Raspberry Pi forum, I can search there for answers.

---


---
title: "Adding swap space to my new install"
date: 2012-11-14
forum: General Help
---

### Post by cokaznrebel on 2012-11-14
To preface this, I would say that I am a Ubuntu newb, and have only been using this for fun for a while, never seroiusly got into the workings of the system.

I installed ubuntu 12.04.1 32 from a live cd to my 64 GB USB Drive that I was not using. When I installed, I wasn't sure what to do about SWAP so i decided to install it without any. I want to add swap now.

So far what I did was
-Shrink the NTFS windows installation on the local hard drive
-created a 6 GiB SWAP partition

Now I have no idea what to do next,
Please help!

---

### Post by acimi66 on 2012-11-14
have a look at this:

[http://www.thegeekstuff.com/2010/08/how-to-add-swap-space/](http://www.thegeekstuff.com/2010/08/how-to-add-swap-space/)

let us know how it goes

---

### Post by Mr_JMM on 2012-11-14
6GB swap is a lot. 4GB is really teh max you'd need unless you were going to use hibernate a lot and even then I believe the most it would use is about 40% of total RAM. Popular consensus is the more physical RAM you have the less need for swap.

Any hoo, can you confirm how many drives you have? It sounds like two - one with windows and now swap and a second USB with Ubuntu; is that correct?
If so, swap works so much better on a second drive so bravo for that.

But I'm not sure what you mean by what next? You mean how to get Ubuntu to see the swap? A reinstall without formatting anything will do it, selecting and marking the swap partition.

I'm not 100% sure if Ubuntu will automatically see the swap ona second drive. Maybe someone can confirm that one way or another.

[edit] Ok, you got an answer as I was writing this. Hopefully that will point you int eh right direction.

---

### Post by oldfred on 2012-11-14
If you have 4GB or more of RAM you may never use swap unless hibernating or editing video. And if hibernating with dual boot, you need to close many programs down anyway to avoid issues and close files in any shared partitions with Windows.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

You actually do not want to use swap as it is at least 10 times slower - hard drive is slower than RAM.

---

### Post by cokaznrebel on 2012-11-14
I have Ubuntu Installed on a 64GB Flash Drive, and the laptop has one 500GB Internal Hard Drive with Windows 7 Installed on it. I just borrowed a few gigs from that install and created a new partition for swap, but ubuntu does not recognize the swap partition because its on a different drive than the installation (USB)

---

### Post by sandyd on 2012-11-15
> **cokaznrebel said:**
> I have Ubuntu Installed on a 64GB Flash Drive, and the laptop has one 500GB Internal Hard Drive with Windows 7 Installed on it. I just borrowed a few gigs from that install and created a new partition for swap, but ubuntu does not recognize the swap partition because its on a different drive than the installation (USB)

that large eh?

Create swap if not done already
```

sudo mkswap /dev/sdxx

```
Mount swap
```

sudo swapon /dev/sdxx
```
replace the sdxx with your drive stuff that corresponds to the drive on your laptop when you boot from usb

---

### Post by mikewhatever on 2012-11-15
> **cokaznrebel said:**
> To preface this, I would say that I am a Ubuntu newb, and have only been using this for fun for a while, never seroiusly got into the workings of the system.

I installed ubuntu 12.04.1 32 from a live cd to my 64 GB USB Drive that I was not using. When I installed, I wasn't sure what to do about SWAP so i decided to install it without any. I want to add swap now.

So far what I did was
-Shrink the NTFS windows installation on the local hard drive
-created a 6 GiB SWAP partition

Now I have no idea what to do next,
Please help!

This is a bad idea. You'll most likely never need that much swap, and possibly won't need any of it at all.

---


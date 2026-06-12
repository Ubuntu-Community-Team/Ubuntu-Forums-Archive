---
title: "Re-installed 7.10, everything lags"
date: 2008-05-04
forum: General Help
---

### Post by javi0084 on 2008-05-04
I had to re-install 7.10 because 8.04 was a bust (at least for me) but now everything lags. Examples:

1.Everything paused as I was typing this, was OK after a few seconds.

2.Browsing through my pictures was OK, everything would pause every few pictures though.

3.Loading pages in Firefox is fast as usual but I have to wait a few second to scroll down or click a link within the page.

4. Switching between windows takes a few seconds (switching between System Monitor window and my Home folder).

5.I went to the drop down menu of "Place" at the top of my screen and everything locked up for several minutes. I had to press and hold the power button to shut of.

Sometimes when it's locked up, my monitor will dim and for a few seconds then everything goes back to normal.

CPU history does show spikes from 2% to 100%. User memory stays constant at 327MB of 1.8GB, SWAP stays at 0 bytes of 4.6GB.

My processor is an AMD Athlon 64 X2 Dual Core Processor 3800 and I have 2GB RAM.

The ISO that I used to install is Ubuntu-7.10-Desktop-amd64.iso

Any help is much appreciated.

---

### Post by javi0084 on 2008-05-05
I have to use Windows for the time being :(

---

### Post by javi0084 on 2008-05-05
Windows just started doing the same exact thing right now so it must be a hardware problem. Ubuntu and Windows sit on their own hard drive so it can't be that.

Can anyone recommend what software to use to run hardware tests?

---

### Post by Monicker on 2008-05-05
First, I would check for diagostics tool from the maker of your hard drive.  Sometimes when they start to have problems, you will get delays because of timeouts and the OS has to try rereading the data from the drive.

---

### Post by javi0084 on 2008-05-05
> **Monicker said:**
> First, I would check for diagostics tool from the maker of your hard drive.  Sometimes when they start to have problems, you will get delays because of timeouts and the OS has to try rereading the data from the drive.

But both Ubuntu and Windows started doing the same thing and they each have their own hard drive. Unless both drives could be going bad? IDK, I was thinking maybe the RAM?

---

### Post by Monicker on 2008-05-05
> **javi0084 said:**
> But both Ubuntu and Windows started doing the same thing and they each have their own hard drive. Unless both drives could be going bad? IDK, I was thinking maybe the RAM?

Oops.  I missed that they were on different drives.  You can run memtest from the Ubuntu CD to check the ram.

---

### Post by javi0084 on 2008-05-06
> **Monicker said:**
> Oops.  I missed that they were on different drives.  You can run memtest from the Ubuntu CD to check the ram.

I ran the memory test from the Ubuntu CD and it showed an error so I took out the RAM that I added about a month ago and all seems fine :)

Thanks!

---


---
title: "Host Protected Area.... rootkit?"
date: 2007-04-23
forum: General Help
---

### Post by Grey on 2007-04-23
I have a Toshiba Satellite M50-YK4.  A couple of months ago, I upgraded to Feisty.  It all went well, and I've had no real problems, aside from this.

I have a couple of video files that I downloaded a while ago, (March 21), that I tried to watch a few days later.  There was a chunk (about a second long) in the middle of a couple of them that would lock up VLC, and every other media player I tried.  After fighting with it for a while, I realized that it was an I/O error that was causing them to pause for very long times while they retried.  I would get a whole bunch of errors like this in dmesg:

```
Apr 23 00:28:59 localhost kernel: [87624.916000]          res 51/40:08:3c:70:72/00:00:00:00:00/ea Emask 0x9 (media error)
Apr 23 00:28:59 localhost kernel: [87624.924000] ata1.00: ata_hpa_resize 1: sectors = 194980905, hpa_sectors = 195371568
Apr 23 00:28:59 localhost kernel: [87624.924000] ata1.00: Host Protected Area detected.
Apr 23 00:28:59 localhost kernel: [87624.924000]      current size : 194980905 sectors (99830 MB)
Apr 23 00:28:59 localhost kernel: [87624.924000]      native  size : 195371568 sectors (100030 MB)
```


There's about 200MB of space that's locked away in a HPA.  I am a little concerned by this, as it seemed to have appeared AFTER I downloaded said movies.  But quite honestly, I'm still new enough to linux that I have no idea how to troubleshoot this, or check for the presence of a rootkit.

---

### Post by bananabob on 2007-04-24
I don't believe that you have a rootkit, but you can install rkhunter with synaptic and use that to check for rootkits

---

### Post by Grey on 2007-04-24
Thanks for the tip.  I ran it, and it gave me a few warnings, about files to check.  I gave them a check, and didn't find anything unusual... but not sure what to look for.  It also told me that root was allowed SSH access, which I thought was odd.  I disabled that.

So what do you suppose could have created the HPA, and how can I disable/remove it?

---

### Post by bananabob on 2007-04-24
Sorry - that is a question for someone a little more technical than me.

---

### Post by Grey on 2007-04-25
Fair enough.  Thanks for your help anyway.  I'm sleeping a lot easier knowing that the 200MB does not seem to be malignant, anyways.  :)

---


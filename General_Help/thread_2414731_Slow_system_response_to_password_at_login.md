---
title: "Slow system response to password at login"
date: 2019-03-14
forum: General Help
---

### Post by richgil2 on 2019-03-14
I am running 16.04 LTS on a 12 year old AMD system. dmesg tells me it is running at 4389.11 BogoMIPS. The system monitor tells me it is using 4.6GB of the available 5.6GB, and almost no swap. The interactive response seems terribly slow: it takes one or two seconds to respond to each character in my password when I log in after booting, and longer if I log back in when the screen saver is running on a system with a active browser (Firefox).
I would like to identify the reasons for this and to figure out how well-endowed a replacement system will need to be to show any significant improvement.
Apologies if I'm posting in the wrong place or asking a question that's already answered. All responses gratefully received!

---

### Post by Autodave on 2019-03-14
Did this installation ever work properly?  Is this a problem that just started or did you just install?

Please give us specs on the computer and exactly what *buntu you installed.

---

### Post by richgil2 on 2019-03-17
Thank you for your quick reply: I was expecting it to trigger an email, but as it did not, I have only just checked for a response: sorry. 

Clippings from dmesg: please ask if you would like something else.
'AMD'

---

### Post by richgil2 on 2019-03-17
Thank you for your quick reply. The following are grepped from dmesg. Please ask if you would like something else. I'll check for a response more quickly too.
'AMD' Sempron 3800+ (1 cpu core)
'Memory' 5730000k/6028792k
'swap' 
3905532k (dev/sda5) + 
5898236k (/dev/mapper/fedora00-swap) + 
2359292k (dev/mapper/fedora-swap)
'Ubuntu' Linux version 4.15.0-45-generic gcc 5.4.0 Ubuntu 5.4.0-6ubuntu1-16.04.10

Installed on a 50G mapper partition on a hard disk, approx half-full.

I think the installation has always been unresponsive, although it is noticeably worse if I leave the browser running: the real memory usage reaches  80-90% and it starts using swap, and then it is very slow indeed.

---


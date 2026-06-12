---
title: "Ubuntu Freezing after Resuming"
date: 2015-07-17
forum: General Help
---

### Post by Chuckn2x on 2015-07-17
Every time I suspend and resume my Chromebook C910, it freezes. The issue exists with both the 3.19 and 4.0 kernel. Sometimes I can access dmesg after resuming, and when I can I usually get something along these lines:

> ata1.00:exception Emask 0x0
ata1.00:failed command: WRITE FPDMA QUEUED
ata1:hard resetting link
ata1: link is slow to respond
ata1: COMRESET failed

Please note that isn't the complete error message, but what I can make out from the blurry pictures I took of the screen. The screenshot tool fails to open once that happens. There are no errors to be found in /var/log/syslog and kern.log

After that message, if I attempt to input anything in the terminal, I get segmentation faulting or I/O errors. Eventually, it just hard freezes and I have to hold down the power button. The laptop performs perfectly fine as long as I don't suspend it (aside from some random wifi disconnects). I've read that the Acer C720 had similar issues and attempted to apply those fixes, but they didn't do anything. 
Those fixes can be found here [https://plus.google.com/+PedroLarroy/posts/6CgQypQukMa](https://plus.google.com/+PedroLarroy/posts/6CgQypQukMa) and here [https://philipalban.wordpress.com/2014/04/25/fixing-suspend-in-xubuntu-on-the-acer-c720-a-simplified-guide/](https://philipalban.wordpress.com/2014/04/25/fixing-suspend-in-xubuntu-on-the-acer-c720-a-simplified-guide/).

Any ideas on how to approach the issue? 

Specs:
Acer Chromebook C910
i5-5200U
Intel HD 5500
ZTC 120GB M.2 SSD
Ubuntu 15.04

---

### Post by Chuckn2x on 2015-07-18
bump

---


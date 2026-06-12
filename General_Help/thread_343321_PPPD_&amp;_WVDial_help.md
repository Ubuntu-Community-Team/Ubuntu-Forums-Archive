---
title: "PPPD &amp; WVDial help"
date: 2007-01-21
forum: General Help
---

### Post by EmilyRose on 2007-01-21
Hi there, I'm trying to get gkdialer or gnome ppp set up. I was using wvdialer, but am now getting an error message about pppd, exit code 8. Basicly, it connects then immediatly hangs up... wvdial WAS working just a couple hours ago - then I updated my system, and installed gnome ppp, and bam! it quit... I've managed to connect to the internet NOW by using pppconfig and pon. Any ideas on what went wrong, and how to fix it? 

Lots of thanks in advance!!

---

### Post by erugalatha on 2007-01-27
Hi EmilyRose,

Have exactly the same problem after installing gkdialer ... my internet access thru a softmodem was working fine but I had to type in commands each time to enable the driver for my modem and then call wvdial too.  So I was looking for a gui that would do all that for me .... gkdialer was recommended but after I installed it wvdial could no longer connect with exit code 8 - then exit code 2.

I've used another computer that has wireless access to download the wvdial tar.gz 1.56 now so I'm going to remove wvdial from ubuntu and reinstall it.  My modem seems to be still detected fine so I just think it's something to do with ppp configuration files in /etc/ppp/peers which gkdialer created and wvdial then somehow started to try to use.

---


---
title: "hard lock - caps &amp; scroll lock lights blinking"
date: 2008-02-20
forum: General Help
---

### Post by KhaaL on 2008-02-20
Greetings

I've had quite the hard freeze today, the first of this kind... Scroll lock and caps lock lights on my keyboard kept blinking, and the magic keys didn't work to reboot the system. What does the blinking mean? and is there other signals that the kernel gives through the keyboard LEDs?

---

### Post by KhaaL on 2008-02-21
bumping

---

### Post by bchandonnet on 2008-02-23
I have had the same issue on two of my machines.  It seems to happen after they sit idle for a while. I hope someone knows what is causing this, and can suggest  a solution.

---

### Post by Tristonh1985 on 2008-02-26
I'm having the same problem here.. the only thing that seems to be the same every time that it happens is that I'm using my wireless adapter and extensively accessing the internet.

---

### Post by jimbofluffy on 2008-04-26
This happen to we with 7.10 and still happens with 8.04.  I am connected to a wireless network and either try to download a package or use firefox for a while and it will eventually freeze with scroll and shift keys blinking.

---

### Post by jszzang on 2008-05-13
I have no wireless device on my desktop and same thing keeps happening on 8.04 :-(

---

### Post by jaykayess on 2008-05-21
This is happening to me too (and other people I work with) on our Dell D630 laptops.  The computer doesn't need to be sitting idle.  It does seem to happen only when using the wireless.  Didn't happen with Feisty.

Entire system freezes with capslock and scrllock blinking.

---

### Post by jimbofluffy on 2008-05-22
I ordered a new wireless card, a netgear, which wasn't recognized by Xubuntu, so I used Ndiswrapper.  I no longer get the lockups when using wireless.

The other card, a Linksys, works fine on a windows box, so it appears the problem I was having is probably taht the auto drivers in Ubuntu or Xubuntu did not work well with the card.

---

### Post by dypang on 2008-05-23
It's happening to me these days, really annoying because it is unpredictable. I'm using a DELL D630 with Fedora 8, kernel 2.6.24.7-92.

I've cleaned the fun although I don't think it is because of the temperature of CPU.

I've test the memory using memtest86+. The memory has no problem.

I've used this system for months, and this problem started only recently. I guess it is because of the wireless:

1: I only have this problem in office, never at home.

2: I've updated the NetworkManager about 1 month ago. Although not sure it is the reason or not, I feel this is the time when this problem starts.

my wireless adapter is DELL 1390 Wlan minicard.

---

### Post by kernalpanic! on 2008-06-05
blinking keyboard lights means you had a kernel panic.  use kdump to dump the kernel and figure out what is causing the panic.

---

### Post by conradcliff on 2008-06-13
I just installed 8.04 and I'm having this same issue. I haven't tried anything but a bit of surfing (locked after about 1 minute) and downloading all the recent updates. I'm using a wireless connection to my network. I will try to disable the wireless and do a few more operations with the system to see if I can get it to lock up...being a newbie I'm not sure how to use kdump..

---

### Post by wgbuntu on 2008-06-23
I'm having this problem too with new DELL 1525, wireless and deluge.  I am using ndiswrapper wlan0: ethernet device 00:1f:e1:8a:b2:83 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: '', 14E4:4315.5.conf
but it makes no difference.  My laptop usually freezes when I'm not watching   
because it is a server.  Problem doesn't happen every day but more than once a week.

---

### Post by luckj on 2008-06-23
> **wgbuntu said:**
> I'm having this problem too with new DELL 1525, wireless and deluge.  I am using ndiswrapper wlan0: ethernet device 00:1f:e1:8a:b2:83 using NDIS driver: bcmwl5, version: 0x4aa190c, NDIS version: 0x501, vendor: '', 14E4:4315.5.conf
but it makes no difference.  My laptop usually freezes when I'm not watching   
because it is a server.  Problem doesn't happen every day but more than once a week.
I've never use wireless adapter but my machine is affected to this problem as well. I was surgfing the web and seems that should be an hardware problem, how can I check it? The flashing leds block the PC randomly and I need to shut down with the "botton".

luckj

---


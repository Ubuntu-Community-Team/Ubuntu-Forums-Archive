---
title: "Troubles finding/installing driver for wifi"
date: 2012-12-31
forum: General Help
---

### Post by elliem on 2012-12-31
Hello,

I'm using Ubuntu 10.04 LTS and I've started using it only recently. However I'm having a problem with my wireless connection. There are no connections available and there is a red ! where the little icon should be.
I thought it could be a driver issue because everything works on Windows on the same laptop. So I ran sudo lshw -C network and there was UNCLAIMED at the top which (according to an article I read) means that there is no driver loaded.
To check which device I typed lspci (in terminal) and i got:
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

I can't connect to the Internet anyhow on Linux, however I have another laptop which is functioning properly so I can download things from there.

Can I have any assistance in installing this driver?
I already checked if ndiswrapper is intalled and it is.

Thanks in advance,
elliem

---

### Post by Cheesemill on 2012-12-31
Is there a particular reason that installed 10.04, it's only supported for a few more months.

If you install 12.04 instead you will get 5 years of support and there is a good chance that your wireless will work straight away as newer versions have support for more hardware built in.

---

### Post by sudodus on 2012-12-31
I found this thread about the same issue. Maybe it will work for you too.

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?p=10082332[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10082332")

Otherwise I think it is a good idea to try a newer version of Ubuntu, or a lighter version Lubuntu or Xubuntu. Try 12.04 LTS, which is 2 years newer and has much better built-in drivers for wifi devices.

End of life of Ubuntu 10.04 is April 2013.

---

### Post by elliem on 2012-12-31
Well... I installed this version 2 years ago and I sort of neglected it because of this very problem. I will attempt to install a newer version and come back to let you guys know how it went.

---

### Post by Pjotr123 on 2012-12-31
> **elliem said:**
> Hello,
I already checked if ndiswrapper is intalled and it is.


It shouldn't be, not for a Broadcom chipset. :)

When you launch a LiveCD session of Ubuntu, you'll be notified *in the live session* about the presence of an installable driver for Broadcom. Do so *in the live session*, and only then install Ubuntu on your hard drive.

Choose preferably 12.04.1 LTS, and you might prefer Xubuntu 12.04.1 over main Ubuntu, if you don't like desktop environment Unity.

---


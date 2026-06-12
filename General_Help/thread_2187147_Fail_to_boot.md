---
title: "Fail to boot"
date: 2013-11-11
forum: General Help
---

### Post by satimis on 2013-11-11
Hi all,

Ubuntu 12.04 fails to boot

BusyBox v.1.18.5(Ubuntu 1:1.18.5-1ubuntu4.1) build-in shell (ash)
Enter 'help' for list of built-in commands
(initramfs)

Please advise how to fix the problem.  I can boot a live-usb to start Ubuntu 12.04

Thanks

B.R.
satimis

---

### Post by Psil0cybin on 2013-11-11
Having the same problem but on Ubuntu 12.04 What can I do
I tried nomodeset

---

### Post by satimis on 2013-11-11
> **Psil0cybin said:**
> Having the same problem but on Ubuntu 12.04 What can I do
I tried nomodeset
Hi,

I fixed my problem as follows.

1)
Following;
Boot-Repair
[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

to install Boot-Repair (I installed it on live-usb)

After installation finished the software started to work automatically fixing the problem (IIRC answering YES to all questions).  


2)
After 1) above finished removed the live-ubs and booted the PC.

Ubuntu 12.04 revived but unable to connect Internet.  Then I followed;
4 Answers (29)
[http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf](http://askubuntu.com/questions/137037/networkmanager-not-populating-resolv-conf)


Please tried to fix your problem.  In case encountering difficulty google search will help you.

Good luck

satimis

---


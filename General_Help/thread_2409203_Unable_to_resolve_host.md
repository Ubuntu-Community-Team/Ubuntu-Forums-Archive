---
title: "Unable to resolve host"
date: 2018-12-29
forum: General Help
---

### Post by siegfried.fink on 2018-12-29
Hi! I'm really new to ubuntu and I understand very little. I'm having the "unable to resolve host" error. I searched for solutions but I can't get it to work. It seems like my case is a little different because I get the message when I'm starting the computer and it gets stuck in loading screen. So I can't (or don't know how to) do nothing. I can't open the terminal, or write or edit files. 
Any ideas? Thanks a lot!

---

### Post by TheFu on 2018-12-29
How name resolution works is different based on the release running and the flavor (xubuntu, lubuntu, kubuntu, ubuntu-gnome, ubuntu-mate, etc... ).  It is how all computers do the look up for google.com --> 172.217.3.238. It can also go backwards, called a reverse lookup. It uses a few layers to solve the lookup problem. First it checks locally, then it uses local services, then it uses internet services. Internet "DNS" services can be manually configured or a few DNS servers might be provided by the DHCP process when the computer initially connects to the local LAN router.

The lookup problem could be a trivial issue for someone with a few years of experience, but for someone **very** new, all the corrective steps might be too difficult.  The solutions aren't likely to be point-n-click and using those other OSes hasn't provided the necessary background.

The easiest answer is to try a different release, perhaps 16.04.5 Kubuntu or Ubuntu-Mate.  Many things related to networking have been changed in 17.10 and later releases.  It is possible that answers provided during an installation were wrong, so the DNS wasn't setup correctly.  When someone is new, it is hard to help troubleshoot because completely unrelated answers could be the issue.  Also, the problem could be with external equipment.  We just can't tell from here.

Did the network work during the installation?

---

### Post by vidtek on 2018-12-30
> **siegfried.fink said:**
> Hi! I'm really new to ubuntu and I understand very little. I'm having the "unable to resolve host" error. I searched for solutions but I can't get it to work. It seems like my case is a little different because I get the message when I'm starting the computer and it gets stuck in loading screen. So I can't (or don't know how to) do nothing. I can't open the terminal, or write or edit files. 
Any ideas? Thanks a lot!

The fu's suggestion is your best bet:popcorn:.  For cutting-edge hardware support try Ultimate Edition, it's based on Ubuntu so you still have access to solutions posted here for issues.  I have yet to find any fancy-pants new-fangled hardware not supported by UE, including some very esoteric USB ac wireless dongles that no other distro seems to recognise.  The only problem with UE I have had is a USB stick install regularly failing, and I have had to revert to burning a DVD:(.

Best of luck, Tony.

---

### Post by HermanAB on 2018-12-30
'unable to resolve host' means that you have a domain name server (DNS) problem.

This may not be the only problem, since a DNS problem should time out, after which the boot process should continue on its merry way.

So, your machine likely has more problems than what is evident on first glance.  Since you do not have much experience yet, I would therefore recommend re-installing with a current version of Linux.

---


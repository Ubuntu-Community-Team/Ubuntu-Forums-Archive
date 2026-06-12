---
title: "FireWall and Anti-Virus"
date: 2006-12-28
forum: General Help
---

### Post by chrispche on 2006-12-28
Just a quick question. Is it really necessary to install a FireWall and Anti Virus software? Is yes, what do you recommend?

---

### Post by AlanRogers on 2006-12-28
Firewall = use a router, giving you NAT & SPI hardware firewall
A-Virus = no real need, just don't open attachments and make sure you MD5Sum all downloads

Why slow your machine down with such software?

---

### Post by scoon on 2006-12-28
Hey there, 

I only use a firewall, firestarter.

-scoon

---

### Post by viper on 2006-12-28
> **chrispche said:**
> Just a quick question. Is it really necessary to install a FireWall and Anti Virus software? Is yes, what do you recommend?

Its not necessary to use AV but it would be beneficial in case you fwd an infected attachment to a windows box  that has no effect on a Linux box. Thats probably a legit enough reason to use AV!
Automatix can install the appropriate software. Check the link out.
[http://getautomatix.com/wiki/index.php?title=Main_Page](http://getautomatix.com/wiki/index.php?title=Main_Page)

---

### Post by viper on 2006-12-28
> **AlanRogers said:**
> Firewall = use a router, giving you NAT & SPI hardware firewall
A-Virus = no real need, just don't open attachments and make sure you MD5Sum all downloads

Why slow your machine down with such software?

The kernel has an inbuilt firewall, firestarter is just a front end, so your not going to slow down your machine.

---

### Post by OffHand on 2006-12-28
Get a hardware Firewall  (router) and screw the AV crap, you won't need it.

---

### Post by kazuya on 2006-12-28
Clamav antivirus is a good one. You do not really need it on linux, but if you use Samba to share files with a windows PC or share files with other window users, It does not hurt to have Clamav to scan a downloaded multimedia file before sharing it with a windows user. As their machine or that windows machine may not be able to handle such an infected file once open. On your Ubuntu or linux PC, you have no need for the anti-virus software.

Firewall is typically already very functional. I would recommend firestarter or guard dog, although, I do not use either or any of these. The OS typically comes secure.

---

### Post by chrispche on 2006-12-28
Thanks. I have a hardware firewall in my router. Which is from the UK and I don't know if it's compatible with the South African phone system. Right now I'm on bloody dial up, because South Africa is so behind when it comes to the internet. It's taking me days to install and setup my ****. Oh well we press on. No need for an AV? Good, one less thing to download.

---

### Post by OffHand on 2006-12-28
> **chrispche said:**
> Thanks. I have a hardware firewall in my router. Which is from the UK and I don't know if it's compatible with the South African phone system. 

A firewall is a firewall  ;)

---

### Post by chrispche on 2006-12-28
So a router with a firewall from the UK will work in South Africa. I can't just use the firewall part of it, with out routing through the internet with it. Anyway is doesn't matter firestarter will suffice.

---

### Post by AlanRogers on 2006-12-28
I'd be very surprised if the router didn't work in SA. ADSL broadband is broadband the world over and the firmware of the router will have options. I am however checking with an SA friend who works for an ISP and lived over here. He'll know and I'll post back later.

---

### Post by cj100570 on 2006-12-30
> **viper said:**
> Its not necessary to use AV but it would be beneficial in case you fwd an infected attachment to a windows box  that has no effect on a Linux box. Thats probably a legit enough reason to use AV!
Automatix can install the appropriate software. Check the link out.
[http://getautomatix.com/wiki/index.php?title=Main_Page](http://getautomatix.com/wiki/index.php?title=Main_Page)

I have to agree with you completely Viper. It's "currently" not necessary to run AV software on Linux. But, and it's a big but, I think that we in the Linux community have become a little to complacent about this issue. I'm sure that some malcontent is hard at work trying to devise a virus for Linux and is counting on our continued belief that we're not at risk to deliver the payload onto a machine. My personal belief is that "everyone" should run AV software just in case. Sure, there's a small resource price to pay for running such software but in the end it may save your machine.

---

### Post by pseudonym on 2006-12-30
> **cj100570 said:**
> Sure, there's a small resource price to pay for running such software but in the end it may save your machine.

Exactly. And not just your machine, but much more likely the machines of others. It's not particularly nice to unwittingly email a linux-irrelevant windows virus to one of your windows-using friends/colleagues, when you had the opportunity to kill it by simply scanning your mail.

This is a silly debate. I've never understood the resistance some people have to adding a simple security layer that is trivial to set up and maintain like an AV. Is it possible to cause harm by *having* an AV? No (entirely separate from causing harm *despite* an AV, of course, but that's hardly the point). Is it possible to cause harm by *not having* an AV? Yes. The equation seems a simple one to me ;)

My recommendations? [F-Prot]("http://www.f-prot.com/support/helpfiles/unix/workstation/index.html") for AV. It's not in the Ubuntu repos anymore, but I find it a tad simpler to use than [ClamAV]("http://www.clamav.net/"), which is.

And [FireHOL]("http://firehol.sourceforge.net/") for your firewall. It's a simplified configuration language for the built-in iptables, with a great tutorial even a relative novice could follow.

---


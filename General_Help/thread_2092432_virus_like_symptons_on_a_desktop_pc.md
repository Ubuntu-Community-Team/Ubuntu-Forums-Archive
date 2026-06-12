---
title: "virus like symptons on a desktop pc"
date: 2012-12-07
forum: General Help
---

### Post by harlie on 2012-12-07
Have read several places that linux is immune to viruses. But my desktop (a 2001 model or there abouts) HP has since upgrade to 12.04 shown virus like symptoms and reverting to earlier releases that originally worked well now give problems. A couple of examples:
software installed from the ubuntu site not installing or not working after install: usb port sometimes works other times not (have to restart wusb) at various times: hard drive suddenly takes off running and without command, during these times no input to pc is accepted or acted on: google earth is unusably slow, and will not install in 11.10 by any of the on line instructions or auto install from google earth site. These are a few of the things that come to mind. Has anyone any comment?

Harlie

---

### Post by dcstar on 2012-12-08
> **harlie said:**
> Have read several places that linux is immune to viruses. But my desktop **(a 2001 model or there abouts**) HP has since upgrade to 12.04 shown virus like symptoms and reverting to earlier releases that originally worked well now give problems. A couple of examples:
software installed from the ubuntu site not installing or not working after install: usb port sometimes works other times not (have to restart wusb) at various times: hard drive suddenly takes off running and without command, during these times no input to pc is accepted or acted on: google earth is unusably slow, and will not install in 11.10 by any of the on line instructions or auto install from google earth site. These are a few of the things that come to mind. Has anyone any comment?

Harlie

[LIST=1]
[*]PC hardware is ancient and not supported by 12.04
[*]PC hardware is going faulty.
[*]Hard disk is going faulty.
[/LIST]

---

### Post by spec36 on 2012-12-08
2001, Sounds like its time for a new desktop. A newer system will feel like a ferrari for you :)

---

### Post by sloe on 2012-12-08
> **dcstar said:**
> [LIST=1]
[*]PC hardware is ancient and not supported by 12.04
[*]PC hardware is going faulty.
[*]Hard disk is going faulty.
[/LIST]

I'd agree with this sentiment - an 11-12 year old hard drive is running on nothing more than sheer faith.

---

### Post by 3rdalbum on 2012-12-08
Definitely not virus-like symptoms. Viruses these days are either overt (popping up advertisements or warnings that "your computer has viruses, you need to buy AntiVirusPro 2011 for only $79.95 to fix it") or display no symptoms.

It's very possible for USB ports to work sporadically due to impending hardware failure; it's happening to my computer which was built in 2007. Hard disk problems would explain sporadic failures to install software, and normal systems such as the Update Manager or desktop search indexing would explain high I/O usage at random times. On such an old computer, this high I/O would cause the computer to get unusably slow.

Google Earth is slow because it's fairly graphically-intensive compared to what graphics chips were available in 2001. It's also very probable that Ubuntu doesn't have drivers for such an old graphics card, and you're stuck on software rendering.

---

### Post by Wim Sturkenboom on 2012-12-08
With regards to your virus like symptoms. You can download diagnostic tools of the HD manufacturer (often can be run as liveCD) to check your HD and you can run memtest from a Linux install CD to check the memory ofyour PC. If those tests report problems, you know you have a hardware problem. If they don't report problems, the tests are non-conclusive.

**Linux is not immune to viruses :)** But the security model **can** limit the effects and there is a lesser amount of viruses for Linux in the wild. But nothing helps if you download some_malware from some untrusted site, read the instructions how to install (please run *_sudo ./some_malware_*) and do as instructed.

A script with a couple of lines of code (that you run with root permissions) can wipe your whole harddisk and any connected external harddisks (that you use for backups). Not very useful for a virus (it wants to spread) but for something that just wants to cause havoc it does succeed.

---

### Post by mörgæs on 2012-12-08
How does it run in a live boot of Lubuntu? 

My guess is that a) you are running a system which is too heavy for the hardware and b) the upgrade (as opposed to a fresh install) messed something up.

Like posted above it's unlikely that a virus has infected the computer.

---

### Post by harlie on 2012-12-08
> **mörgæs said:**
> How does it run in a live boot of Lubuntu? 

My guess is that a) you are running a system which is too heavy for the hardware and b) the upgrade (as opposed to a fresh install) messed something up.

Like posted above it's unlikely that a virus has infected the computer.

Thanks for all the input. It lays out a banquet for thought, I chose Ubuntu liked it and never have changed. Have not tried Lubuntu though I think I have the disk. My other pc has Ubuntu alsothat is why I want to keep Ubuntu so I can experiment and not hurt the main one with my important stuff on it.

Harlie

ps. The install disk will not work on this computer I even got a replacement thinking the previous disk was defective but the only way I could get 12.04 installed was by downloading the upgrade.

---

### Post by harlie on 2012-12-08
To all who replied a great big thanks, I think it is time for a new pc. Staples has a good sale starting Sunday for a lower grade HP that I think will serve my purpose. Has e little less mem but probably more than this one.

Harlie

---

### Post by mörgæs on 2012-12-08
If you want something new this list is worth checking first:
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

Used hardware a few years old is another good option.

---

### Post by Wim Sturkenboom on 2012-12-09
> **harlie said:**
> My other pc has Ubuntu alsothat is why I want to keep Ubuntu so I can experiment and not hurt the main one with my important stuff on it.
If that other PC is capable enough, you can install a second instance of Ubuntu in a virtual machine inside your main Ubuntu. That's how I test certain things, e.g. to help people on the forum; if it gets damaged it's not a big issue.

With regards to important stuff: see my signature ;)

---


---
title: "how do I install Lubuntu 16.04.02 on XP laptop with Wubi?"
date: 2017-05-17
forum: General Help
---

### Post by ardouronerous on 2017-05-17
I have an old XP laptop, the CD drive is busted, although it can boot off USB, booting off USB isn't an option for me because I'd like to save settings and updates and not start from scratch every time I open my machine.

The reason why I want to try Wubi is because, unlike dual-booting, I heard Wubi is easy to install and uninstall.

Purging XP isn't an option too,  because this is a family laptop, my dad still uses XP and some of his programs don't work on Wine, and Virtualbox isn't an option too, this laptop's RAM is only 1GB, not enough memory to share with virtual machine.

---

### Post by wildmanne39 on 2017-05-17
Wubi is long dead and unsupported.

---

### Post by ardouronerous on 2017-05-17
Okay, any other ways of doing it then.
Wasn't there a fork of Wubi?

---

### Post by yancek on 2017-05-17
Wubi was designed specifically to be used to test Ubuntu and not to be used on anything like a long term basis.

If you can boot from a usb, you can use windows software such as pendrivelinux, unetbootin to create a bootable Ubuntu usb and use that to install Ubuntu to your hard drive.  You can use unetbootin to create a persistent install of Ubuntu on a flash drive which will allow you to save changes and data.

---

### Post by wildmanne39 on 2017-05-17
I found this link to a forked version of wubi but I do not recommend it, in fact I discourage its use,
[https://github.com/hakuna-m/wubiuefi](https://github.com/hakuna-m/wubiuefi)

I think it is probably more trouble then it is worth and wubi is only intended as a temporary install.

---

### Post by ardouronerous on 2017-05-17
Back when I first started Linux, my first was Xubuntu 12.04, and I used Wubi on my Desktop for a year before wiping out my Windows XP desktop, and my experience between using a full installation and Wubi was the same, I didn't feel the difference between the two methods.

I do have a bootable Lubuntu USB, but like I said, not really an option because I have to save updates and stuff, and I heard creating a persistent USB is a bad idea because that will break the USB.

I heard there was a fork of Wubi called Wubiuefi, anyone has experience with this?

---

### Post by ardouronerous on 2017-05-17
> **wildmanne39 said:**
> I found this link to a forked version of wubi but I do not recommend it, in fact I discourage its use,
[https://github.com/hakuna-m/wubiuefi](https://github.com/hakuna-m/wubiuefi)

I think it is probably more trouble then it is worth and wubi is only intended as a temporary install.

Okay, thanks for the info.
Why is Wubi only intended as a temporary install?
Like I said in my previous post, I used Wubi with Xubuntu 12.04 for a year before I decided to do a full installation, and my experience with Wubi and a full install is the same, I never experienced any trouble with Wubi.

---

### Post by wildmanne39 on 2017-05-17
Its intended to make it easy for a windows user to try out Ubuntu and see if they like it, then it is meant to be installed.

Yes you can use it longer but you were only lucky that you did not have any issues, look at it this way if you have it on its own partition and windows goes down and you get the blue screen of death, you still have Ubuntu that you can boot and use for daily needs and also to retrieve files from the broken windows system. 

Same if you get a virus, but if it is in a file on your windows partition then both systems are down, and you will have to reinstall windows and when you do you lose Ubuntu.

It is also not normal for Ubuntu to run as well in wubi as it does on its own partition.

---

### Post by QIII on 2017-05-17
WUBI installed Ubuntu in a [loop device]("https://en.wikipedia.org/wiki/Loop_device").  That is, it was not exactly running "inside" Windows, but its universe was in a Windows filesystem.  As part of that file system, the entire installation was subject to the same mechanisms of corruption and destruction as any Windows file.  That is, if you messed up your Windows you stood a good chance of ruining your WUBI Ubuntu.  Forks or not, the original developers of WUBI (who themselves said it was intended to provide an environment for a test drive) stopped developing it and do not recommend its use any longer.

Furthermore, Windows XP is no longer supported and it is vulnerable to any number of threats.  If you have been paying any attention to the news, you will be quite aware of what has been going on this week.

Combine those two things and you have a recipe for disaster.  Providing help with your attempt to do this violates the spirit of Ubuntu and is, at best, irresponsible.

I would highly, HIGHLY, recommend replacing Windows XP with Win7 or Win10 if you are going to keep Windows.  The fact that it is a family computer is no reason to leave XP on it.  In fact, that is probably the very best reason to update it to a secure OS.  Then, if you want to have a Linux system, dual boot.

For the moment, this thread is closed pending Staff deliberation.

---

### Post by QIII on 2017-05-18
Our general philosophy on support is that "It's your computer, it's your choice."  That is, we may recommend against a particular course of action but will allow the community to help with a support request.  We know that people have unique needs and are in unique circumstances. In some cases even non-recommended solutions may be appropriate.  In this case, it doesn't seem that the machine is solely yours.  It's the "family computer", so we aren't dealing just with your interests.

This is a somewhat unusual request in that you are asking for help with Wubi (which was intended for temporary use and which is no longer supported by its original developers) and Windows XP (which is no longer supported by Microsoft and is vulnerable to any number of attacks) in a time when the tech news is filled with horror stories about a cryptolocker-type malware attack and another bot attack playing on the same vulnerability.  You are asking us to not only help you do something we don't recommend, but also something that is significantly more likely to end in harm for you or your family than profit.

You have been given some guidance on where to find a Wubi fork that is purported to work with UEFI (if needed) and to that I will add that with 1GB of memory Lubuntu would be a better choice than Ubuntu.  A dual boot would really be the best choice.

While we wish to provide support for all requests, we also want to do no harm.  Your family also has an interest at stake here.  To that end, after a good deal of discussion among the Staff, this thread will remain closed.

---


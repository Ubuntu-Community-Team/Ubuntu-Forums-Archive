---
title: "iTunes on Ubuntu and all its Official Flavours - HOW?"
date: 2013-12-13
forum: General Help
---

### Post by amjjawad on 2013-12-13
Today, one of my neighbours sent me a message on Facebook asking me about how to get iTunes on Linux? 

I have tried PlayOnLinux and/or Wine = DID NOT help!

Someone suggested to use a Virtual Machine, Install Windows and then install iTunes but I have never tried that and NOT even sure if this will ever work?

HOWTO Install iTunes on Ubuntu and any of its official variants??? so that iTunes actually 'WORK' not just be installed :)

Thank you!

---

### Post by TREESofRIGHTEOUSNESS on 2013-12-13
This is something I have also been very interested in finding out.  My wife has iPhone, and it is not smart enough to recognize music without iTunes.
I think if you have a windows disc, it might be possible to make a BartPE (or similar) and make a VM out of it.  I have not had success using VMWare with XP and iTunes.  I have read somewhere that it is possible with VirtualBox, but I have not had success, yet.  I got so tired of messing around with it that I have given up until I can get a supported OS on some device.  The other thought I have had is by using Google to import tracks into the iPhone, but I haven't really looked into it.  I wonder how iTunes integrates with Google services, or how you would get iTunes music onto an Android.  Personally I never liked iTunes, it is ugly and slow.

---

### Post by plimptm on 2013-12-13
Hello all,

Let me just start this response off by saying that I'm brand new to the StartUbuntu initiative, but I support it wholeheartedly.  I've already converted my wife's Dell Inspiron laptop to Lubuntu (after converting all of my machines in the past year) and am hoping that with the short remaining life of XP I can branch out to other family and friends.  

It is of course critical to do this wisely and "the right way" - making sure that we don't leave anyone out to dry with features and/or functionality missing and a sour taste in their mouths about the Linux community.  We have enough of a reputation already of being inaccessible and too complicated for the everyday user.

In response to the original post, I'm happy to share that I've been successfully running Windows 8 as a VM within my Debian Wheezy machine. The initial reason for me to make this setup work was that I own a Canon multifunction printer/scanner (USB - not a network device), and anyone that's tried to make Canon devices work in Linux knows that it's anything but a straight shot. It proved to be a much more feasible task to run my Windows 8 installation (which I had purchased as an upgrade to the Windows 7 that shipped on my PC) as a VM and use the printing/scanning functionality provided with the Canon/Windows software.

The easiest software for this is Oracle VirtualBox, hands down.  Not only is it free for personal use, but the GUI has full functionality making setup and configuration a breeze. It also allows for USB device redirection, which for me meant my printer could communicate directly with the running Windows VM, and for the Apple fan, their iPod/Pad/Phone can connect directly to the iTunes software running in Windows. I've tested and used iTunes successfully with my wife's iPod, so I can vouch for that as well.

There are of course a few considerations before jumping on board the VM route. Even though my ~2004 IBM Thinkpad with a single core 1.5GHz CPU and 2GB RAM can run Windows XP on top of Debian Wheezy, it's still a bit of a stretch. I would not be able to pull it off with much less RAM. VirtualBox requires you to dedicate an adequate portion of the host memory to the guest machine, so if you're working with a PC that only has 1GB or less of physical RAM, it might not be the most feasible option. Dual (or more) core processors definitely improve the performance of a VM, but aren't necessary as long as the host OS (whatever Linux variant) is not too background process heavy. If the machine in question doesn't have the hardware to pull of a VM, the best option is dual booting - leaving a partition with Windows intact solely for the use of the Windows-only software. Of course if you can convince a friend/neighbor that their PC will be useful for longer than they imagined, it might not be hard to convince them to upgrade their RAM so as to allow for a VM.

I've given this topic a lot of thought and experimentation, so I'd be happy to contribute some more detailed info on how I pulled off the VM scenario, as well as some more "fun" directions this project can go - like how to run an already installed/configured Windows partition as a VM, or set up the Windows VM to logon with a shell using only the necessary application.

This is a super important piece of the puzzle when it comes to making Linux usable right now. I certainly wish we could abandon Windows altogether, but the reality is that many things are simply "made to work" with Windows and almost nothing is "made to work" with Linux.

-Tim

---

### Post by freechelmi on 2013-12-14
Hi 

- Note sure I understood : did you wipe Windows from those people machine ? after asking them they won't be able to use theur software anymore ?

- VirtualBox is the way to go : You can prepare a Windows VM with the needed apps, export to OVA and give the Ova files to anybody that needs those apps

---

### Post by amjjawad on 2014-02-08
> **freechelmi said:**
> Hi 

- Note sure I understood : did you wipe Windows from those people machine ? after asking them they won't be able to use theur software anymore ?

Hi,
I usually tell them that iTunes won't work but some of them when I ask them 'before' I do anything and they say we don't need anything. 'After' I install and finish (no more Windows), they remember to ask about iTunes. So far, they didn't ask me to go back to Windows except one user and I am not sure if he took his laptop to someone else to wipe Linux and Install Windows yet again? or he just got busy and forgot about it. 

Lately, I started to make a [Dual-Booting system]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html"). However, in Windows XP case, I can't because of the EOL of Windows XP. I can dual boot Windows 7 and one of Ubuntu official variant (I'm installing Lubuntu, Xubuntu and Ubuntu GNOME) but can't do the same with Windows XP.

> - VirtualBox is the way to go : You can prepare a Windows VM with the needed apps, export to OVA and give the Ova files to anybody that needs those apps

OVA file?

I am just concerned about the possibility of any kind of security issue. I mean, a VM with say Windows XP which is out dated and that VM is connected to the Internet? how safe that is? I am not really sure as I don't deal with Windows any more.

It could be the best option is Dual-Booting. But I was really hoping for an alternative for iTunes.

Some said "rhythmbox" is way to go but I don't have any Apple device nor I use "rhythmbox" so I don't know about this.

---

### Post by amjjawad on 2014-02-08
> **TREESofRIGHTEOUSNESS said:**
> The other thought I have had is by using Google to import tracks into the iPhone, but I haven't really looked into it.  I wonder how iTunes integrates with Google services, or how you would get iTunes music onto an Android.

Hi and thanks for posting :)

Google and iTunes? this is totally new to me?!

---


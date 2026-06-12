---
title: "Installing VMWare Tools"
date: 2008-04-13
forum: General Help
---

### Post by DoogH on 2008-04-13
Ok, I have read other posts about this issue, and I haven't seen it resolved.  However, I am using VMWare Fusion on my Mac.  It asks me to install VMWare tools in order to use the video card.  However, when I tell VMWare tools to install, it mounts what appears to be a DVD image.  I am not sure if I am supposed to install it from here, or if it is supposed to install itself.  If I am supposed to install it, I cannot figure out how.  I have tried MANY different commands like sudo aptitude install vmware-tools.pl.  Yet, I can't find the package.  Any help in installing the tools would be GREATLY appreciated.  I cannot install a game I want to play without it.

---

### Post by DoogH on 2008-04-13
PLEASE Help me!

---

### Post by DoogH on 2008-04-13
Not a SINGLE response...  Just wow...

---

### Post by DoogH on 2008-04-13
*waits*

---

### Post by farmfield on 2008-04-24
Well, the VMWare-Tools package is available through Synaptic, so you don't have to use it from the "cd" - which is in rpm, right(?), and then you'll need to convert that with the application "Alien" in the terminal a.s.o. - not very fun. Check synaptic first!:)

Aah, and I got the same prob as you though I'm testdriving Kubuntu 8.04 KDE4-Remix where the VMWare-Tools-package isn't available throuch "Adept" (Kubuntu's Packager) and I just refuse to start messing around with "Alien", hehe...

So no help for me but hopefully some for you! Rgds/FF

---

### Post by ebelog on 2008-04-24
I just went through this on Windows, and I think it will work the same way for you on Mac.

1. Clicking on the VMWare Tools Install menu opens a virtual CDROM called /media/cdrom0 with an RPM file as well as a "tarball"
2. Open a terminal by clicking on [Applications] -> [Accessories] -> [Terminal] (I'm more comfortable on the command line, but I'll try to keep it simple)
3. become the root user with the command '[FONT="Courier New"]sudo su -[/FONT]' (type your own password when asked)
4. [FONT="Courier New"]cd /usr/local[/FONT]
5. Unpack the install package (note: the version number may vary)
   [FONT="Courier New"]tar -zxvf /media/cdrom0/VMwareTools-6.0.3-80004.tar.gz[/FONT]
6. Switch to the directory it created
   [FONT="Courier New"]cd vmware-tools-distrib[/FONT]
7. Run the installer script
   [FONT="Courier New"]./vmware-install.pl[/FONT]
8. Choose the defaults as the installer asks you questions.

I know that many people try to avoid the command line as much as possible, but this package has a good install script that makes it easier, so give it a try.

----------------------------
[http://www.ebelog.com](http://www.ebelog.com)

---

### Post by Belathor on 2008-04-24
I tried this a few weeks ago but I managed to mess it up. The vmware-tools script expects i386, but Hardy Heron has x86 instead. So that is why it doesn't work if you try it.

---

### Post by dcstar on 2008-04-25
> **DoogH said:**
> Not a SINGLE response...  Just wow...

Probably because the answer has been posted many times in the Virtualization forum - as a simple search would have shown.

---


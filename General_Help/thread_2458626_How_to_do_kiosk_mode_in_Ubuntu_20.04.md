---
title: "How to do kiosk mode in Ubuntu 20.04?"
date: 2021-02-28
forum: General Help
---

### Post by orangethrift on 2021-02-28
I'm writing a fancy touchscreen app that will run on a tablet running Ubuntu 20.04 x64. The tablet is dedicated to running the app, nothing else is of importance. I'm interested in the easiest way to get my app to run in "kiosk mode". 

So things like:

[COLOR=#000000][FONT=Calibri]
[LIST=1]
[*]At  startup, boot straight into my app in fullscreen mode, without login 
[*]If possible, don't show any desktop even for a fraction of a second. There shouldn't be the concept of a desktop. 
[*]On app crash, auto-restart the app 
[*]Disable all screensavers and locks 
[*]When  the system is powered on, I'd like to show a custom splash screen  during boot with the app's logo, not the Ubuntu boot sequence. 
[*]Prevent user from closing the app (it's a tablet, but it has a USB port so someone could plug in a keyboard and press Alt+F4) 
[/LIST]
[/FONT][/COLOR]

I can hack together solutions to all of these (systemd service/unit file, disabling USB in kernel boot flag, etc), the ones I have no clue about being #2. I'm just wondering if there's a smarter solution designed for this problem that I should be using to do what I want, instead of doing 6 different things manually.

---

### Post by Holger_Gehrke on 2021-03-01
Unless your app needs the infrastructure a full desktop distribution like Ubuntu provides, I'd take a hard look at the way specialist one-purpose distributions like [OpenElec]("https://openelec.tv/") or [retropie]("https://retropie.org.uk/") (both of these are mainly for the Raspberry Pi, but the principles are the same) do things. For 2. you probably want to run pure X without even a window manager (which should also take care of most of 6.).

Holger

---

### Post by dragonfly41 on 2021-03-01
Could an [Electron kiosk app]("https://medium.com/@andreas.schallwig/building-html5-kiosk-applications-with-vue-js-and-electron-c64ac928b59f") meet part of your requirements?

I use Atom editor for Electron app development.

You can develop app to have frameless window.

Further customisation might come from Cubic at a guess.

[P.S.] regarding #5 custom splash screen I find that rEFInd is good for that.
Custom themes then go in [FONT=monospace][COLOR=#000000]/boot/efi/EFI/refind/refind.conf[/COLOR]
[/FONT]

---

### Post by orangethrift on 2021-03-01
> **Holger_Gehrke said:**
> Unless your app needs the infrastructure a full desktop distribution like Ubuntu provides, I'd take a hard look at the way specialist one-purpose distributions like [OpenElec]("https://openelec.tv/") or [retropie]("https://retropie.org.uk/") (both of these are mainly for the Raspberry Pi, but the principles are the same) do things. For 2. you probably want to run pure X without even a window manager (which should also take care of most of 6.).

Holger

I considered this, but: 

a) I would lose the familiarity I already have with Ubuntu
b) it would be less polished/stable than Ubuntu. Ubuntu has tons of engineers working on it and is used by tens of thousands of people, resulting in a very stable, battle-tested whole. My app isn't just a basic display app, it uses a relational  database, runs snmpd, might have to add web APIs one day, etc. 
c) if I ever run into a big problem and need advice, Ubuntu has a huge community and even paid technical support
d) I don't like the idea of the user's OS being different from the developer's OS, it lowers productivity

---

### Post by HermanAB on 2021-03-01
The easiest way to create a kiosk, is to enable the Guest Account.

---

### Post by C.S.Cameron on 2021-03-02
**_GUEST ACCOUNT ON PERSISTENT INSTALL_**

If powering the kiosk with a persistent Live USB see:

[https://askubuntu.com/questions/1223739/how-can-i-make-a-persistent-usb-install-read-only-unable-to-be-modified-after-se/1223764#1223764](https://askubuntu.com/questions/1223739/how-can-i-make-a-persistent-usb-install-read-only-unable-to-be-modified-after-se/1223764#1223764)

You might also want to check out Ubuntu Core: [https://ubuntu.com/core](https://ubuntu.com/core)

---

### Post by deadflowr on 2021-03-02
Related to Ubuntu Core see:
[https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview]("https://ubuntu.com/tutorials/secure-ubuntu-kiosk#1-overview")

---

### Post by HermanAB on 2021-03-02
Lahk ah sed - the Guest Account pretty much *is* a Kiosk system.  Just enable it and you are done.  That will take about 5 seconds tops.

---

### Post by C.S.Cameron on 2021-03-02
Herman
Is Guest Account running on off the shelf 20.04 or do we need to install lightdm first?
I understood Ubuntu switched to GDM with 16.10.

---

### Post by HermanAB on 2021-03-02
It’s been a while since I used it on Ubuntu.  A few years ago, it worked fine.  The same thing is also available on Mac and FreeBSD.

---

### Post by C.S.Cameron on 2021-03-02
It still works fine, as long as lightdm is installed and guest=true is activated.

---


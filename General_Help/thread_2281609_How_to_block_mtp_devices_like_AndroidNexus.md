---
title: "How to block mtp devices like Android/Nexus"
date: 2015-06-08
forum: General Help
---

### Post by Mark_Dart on 2015-06-08
Hi

We have PCs running 14.04 and we want to lock down the USB ports so users cannot steal data.

We have blocked usb_Storage in blacklist.conf and it works; USB drives will not mount at all.

However I noticed that someone's Android Nexus mounts as a storage device and the user is able to copy files. Apparently these devices work through MTP.

May I ask how we can block all MTP devices? I have looked for easy answers but can't find any.

I am a bit of a noob at Ubuntu so may ask many questions, particularly if you talk about an app/component that doesnt come automatically with 14.04

Many thanks

---

### Post by Mark_Dart on 2015-06-10
Hi

have i put this in the wrong forum?

any help with this would be great

thanks

---

### Post by SeijiSensei on 2015-06-10
No, I think it's because most people here don't manage networks where those sorts of controls are needed.

The other problem for me is that I don't know enough about the MTP stack to know what specifically needs to be removed.  From [this](https://wiki.archlinux.org/index.php/MTP), I'd imagine removing libmtp would be a good first step.  You'll probably also need to blacklist the package so it can't be reinstalled; [this](http://askubuntu.com/questions/75895/how-to-forbid-a-specific-package-to-be-installed) looks like it will help.

On my 64-bit 14.04 system the package is called libmtp9:amd64.  It has a dependency on libmtp-common; that probably needs to be removed as well.
```

$ dpkg -s libmtp9:amd64
Package: libmtp9
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 455
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: libmtp
Version: 1.1.6-20-g1b9f164-1ubuntu2
Depends: libmtp-common, libc6 (>= 2.14), libgcrypt11 (>= 1.4.5), libusb-1.0-0 (>= 2:1.0.8)
Pre-Depends: dpkg (>= 1.15.7.2), multiarch-support
Recommends: libmtp-runtime, udev
Description: Media Transfer Protocol (MTP) library
 libmtp is a library for communicating with MTP aware devices in POSIX
 compliant operating systems.  It implements MTP Basic, the subset
 proposed for standardization.
 .
 The Media Transfer Protocol (commonly referred to as MTP) is a devised
 set of custom extensions to support the transfer of music files on
 USB digital audio players and movie files on USB portable media players.
Original-Maintainer: Alessio Treglia <alessio@debian.org>
Homepage: http://libmtp.sourceforge.net/

```

---

### Post by Mark_Dart on 2015-06-10
mate that is really useful, i really appreciate you taking the time to do this.

I'm back there tomorrow and I'll start messing about using your guidance. I'll do it on a test machine of course.

Ill try removing libmtp and also the apt-pinning thing to stop it being re-installed; also considering its what it depends on.

Thank you so much

---

### Post by HermanAB on 2015-06-10
Ultimately, what you want to do is futile.  It is always possible to transfer data somehow: HTTP, FTP, SSH, netcat, ncat, CIFS, SMB, NTP, POP, IMAP, WebDAV, etc.  Even the ping or DNS protocols can be used to transfer data and when all else fails, one can use printscreen or a cell phone camera.

So, good luck with that...

---

### Post by SeijiSensei on 2015-06-10
If this is a locked-down network, most of those protocols will be blocked on any server with sensitive information.  To say the effort is futile assumes no security policy is even worth attempting.  Having worked with a health provider, we have instituted pretty severe limits on what staff members can see and do on the network.  Could someone with sufficient knowledge and intent figure out a way around these limitations?  Perhaps, but policies like disabling USB storage devices would stop most ordinary employees from simply attaching their phones and downloading data.

How exactly would I use POP3 to pull schematics off a Windows Server not running Exchange in a well-regulated Active Directory setup?

---

### Post by simonn on 2015-06-10
In addition to what SeijiSensei said, there is the practicality that servers in 99% of scenarios need to be network accessible so you cannot just turn the network off, just limit what can be accessed to and from the server and audit it.

OTOH, I cannot really think of a reason not to have USB turned off on servers. Stops one headache.

My favorite fallacy :):
[http://en.wikipedia.org/wiki/Nirvana_fallacy](http://en.wikipedia.org/wiki/Nirvana_fallacy)

Defense in depth baby.

---

### Post by Mark_Dart on 2015-06-11
> **HermanAB said:**
> Ultimately, what you want to do is futile.  It is always possible to transfer data somehow: HTTP, FTP, SSH, netcat, ncat, CIFS, SMB, NTP, POP, IMAP, WebDAV, etc.  Even the ping or DNS protocols can be used to transfer data and when all else fails, one can use printscreen or a cell phone camera.

So, good luck with that...

thank you for your response.

I will now consider the futility of doing anything. Might even take passwords off the PCs and the locks off the doors.

genuine thanks.

---

### Post by Mark_Dart on 2015-06-11
> **SeijiSensei said:**
> If this is a locked-down network, most of those protocols will be blocked on any server with sensitive information.  To say the effort is futile assumes no security policy is even worth attempting.  Having worked with a health provider, we have instituted pretty severe limits on what staff members can see and do on the network.  Could someone with sufficient knowledge and intent figure out a way around these limitations?  Perhaps, but policies like disabling USB storage devices would stop most ordinary employees from simply attaching their phones and downloading data.

How exactly would I use POP3 to pull schematics off a Windows Server not running Exchange in a well-regulated Active Directory setup?

Thank you for your actual help in this matter SeijiSensei, it is very much appreciated.

---

### Post by Mark_Dart on 2015-06-11
> **simonn said:**
> In addition to what SeijiSensei said, there is the practicality that servers in 99% of scenarios need to be network accessible so you cannot just turn the network off, just limit what can be accessed to and from the server and audit it.

OTOH, I cannot really think of a reason not to have USB turned off on servers. Stops one headache.

My favorite fallacy :):
[http://en.wikipedia.org/wiki/Nirvana_fallacy](http://en.wikipedia.org/wiki/Nirvana_fallacy)

Defense in depth baby.

many thanks to you too Simonn

---

### Post by Mark_Dart on 2015-06-11
OK I tried to remove the libmtp9 package and it then talked about removing ubuntu desktop and software center which doesnt seem like a good idea.

Someone I spoke to suggested playing about with udev but I am not sure what I am doing with this. 

Does anyone have any further advice?

thanks again

---

### Post by SeijiSensei on 2015-06-11
[Ubuntu-desktop]("http://packages.ubuntu.com/trusty/ubuntu-desktop") is a "meta" package that installs all of Unity as dependencies.  Once the actual software is installed, you can remove ubuntu-desktop itself.   I've had the same experience as a Kubuntu user when I removed kmix, the default volume control app, from my system so I could replace it with plasma-widget-veromix.  Apt told me it would remove kubuntu-desktop as well; it never made any difference.

Removing the software center seems a bit weird since it shouldn't have anything to do with libmtp9.

Even if you removed Software Center, you should still be able to use apt-get to install any software you need.  I rarely use the GUI software managers at all.

I'd just give removing libmtp9 a try and see what happens.  Mucking around with udev is above my pay grade.

---

### Post by Mark_Dart on 2015-06-11
awesome, thanks mate!

im going to give that a go on a test machine when its available on monday (currently at full capacity)

thank you and have a good evening and weekend

---

### Post by Mark_Dart on 2015-06-22
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")

This appears to have worked. Many thanks for your efforts on this. Doing an apt-get didnt reinstall the mtp components and the device continues to be blocked as storage

cheers!

---


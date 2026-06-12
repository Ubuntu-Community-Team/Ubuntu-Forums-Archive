---
title: "Encrypted drive via kvm won't boot except recovery mode"
date: 2015-01-23
forum: General Help
---

### Post by Swiftjay on 2015-01-23
I have a ubuntu server and I'm trying to install a xubuntu machine with full OS encryption via KVM.  When isntalling it seems fine but when I boot up, it won't boot up the OS normally and only boots up the OS once you've gone to recovery mode which is no where near ideal as I need it for a remote desktop and the graphics are disabled.

Has anyone tried to encrypt xubuntu file system before and had this issue?  Any feedback is appreciated.

On another note, if I can't get full system encryption I want to encrypt the **whole** /home folder not just my user.  If I select encrypt home drive does this do that or is it only my account?  If not is there a way to encrypt every users home folder on each account I create?

---

### Post by Swiftjay on 2015-01-26
I've been able to fix the issue.  It was a graphics card problem on my KVM.  I found this article here: [FONT=times new roman] [http://community.linuxmint.com/tutorial/view/842](http://community.linuxmint.com/tutorial/view/842)
[/FONT] [FONT=times new roman]

For anyone else in the future here's a quote of it:

> **Add one** of the following** *'????.modeset=0'* **parameter  at the end of the long grub command line as is (type 1 space before).  Use the parameter related to the brand or chipset of your video card .  pe.: use **nouveau**  or **nvidia** for nvidia based cards (proprietary driver, just **nv** in some linux distributions, nouveau driver is the default in Mint) ), use **radeon** for amd/ati cards, **i915** for intel based motherboards, ,,,  These are the most common examples.   [/FONT]

[LIST=1]
[*]     **nvidia.modeset=0**
[*]     **nouveau.modeset=0**
[*]     **radeon.modeset=0**
[*]     **i915.modeset=0 **
[*]     **r128.modeset=0  **(for very old ati rage 128 cards...)
[*]     If you [COLOR=#00f]don't know the brand [/COLOR]you may use just one word:   **nomodeset**
[/LIST]
[FONT=times new roman]

So: sudo vi /etc/defaults/grub

In the "quiet splash" section so I did "quiet splash nomodeset" 

write quit

Then

sudo update-grub2  then reboot it works!  Will mark thread as resolved.

Will mark this as resolved
[/FONT]

---


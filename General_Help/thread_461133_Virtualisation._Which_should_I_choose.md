---
title: "Virtualisation. Which should I choose?"
date: 2007-06-01
forum: General Help
---

### Post by eentonig on 2007-06-01
I'm on reïnstalling a Desktop PC at home.

Off course, primary OS 'll be Ubuntu Feisty. 

But,  I'll need to have, at least on occasions, access to XP. But the amount off times I'll need that, do not justify to sacrifice a partition/much disk space (or hassle to dual-boot) I plan to run this in a virtual machine.

I'll also plan to regularly install and try some other distro's and ubuntu upgrades.

In the past I've always used VMWare. But that was just because it was the first product I got to know about.

Can someone give me some insight on the pro's and con's of the differen vm suites that are available?

VMWare?
Virtualbox
QEmu?
Others??

What are the befits of using product x compared to y? What are the pitfalls?

---

### Post by smoker on 2007-06-01
i've tred vmware and virtualbox, and found virtualbox the easiest to setup and use, i have four virtual machines set up in virtualbox, and a new one can be added simply.

i haven't tried qemu or any other, i would recommend to give virtualbox a try.:-)

---

### Post by cosbear on 2007-06-01
Howdy:

I haven't tried anything but VirtualBox on feisty, though I have tried some of the others on other distros and found them to be too limiting in various ways.  Mostly just too slow.  But I am really impressed with VirtualBox.  I had a heck of a time getting it to install properly and read somewhere on the forum here to install Automatix and install Virtual Box with that, and it worked perfectly.  Turns out I am really impressed with Automatix as well.  [http://www.getautomatix.com](http://www.getautomatix.com)  Install the Automatix .deb package and then use it to install VirtualBox and it went very easily for me.  Then I installed XP on a virtual drive alIocating 20 gigs for that. I am running it on a dual processor pentium  4 2.8G with 1gig of ram and allocate half that ram to Virtualbox while it's running and neither opperating systems seem to be slowed down appreciably at least not for what I'm doing with them.  I have installed software on XP and worked just like it's supposed to.  I didn't have to set up anything in XP either it came up with everything ready to go.  Configuring Virtualbox was very intuitive and had sufficient help and guidance along the way to make it pretty painless.  I was able to share a directory on the  Ubuntu drive  with virtualbox so all my docs and mp3s and videos are available to both opperating systems at all times.  I've tried other solutions on other distros and always went back to a dual boot system but this is way better as far as I'm concerned.  It's great having unsecure windows floating within the secure arms of Linux.  I won't use Windows much to go online but will feel a little more safe when I need to, like when i used winupdate to update XP.  Worked like a charm.  Good luck.  cosbear

---

### Post by zach12 on 2007-06-01
i use VirtualBox vmware is hard to use

---

### Post by veloce on 2007-06-03
Virtualbox has the most vocal supporters.

VMware under feisty is much easier to setup than it used to be as it is now in the repositories.

Whichever is the first to offer 3d acceleration will get my vote!

---

### Post by cosbear on 2007-06-03
Howdy:

The Quote below is from the VirtualBox  manual and is speaking about the Windows XP guest virtual machine with the Guest Additions installed, which come with the package.  I am running XP as guest on feisty and video acceleration was set as default at 100%.  VBox also allows for multiple displays including sizes and resolutions not even available on most hardware.  Such as very large screens which can stretch over mutiple displays.  I don't really understand all of that nor have a use for it myself but it sounds pretty interesting.


"Better video support.  While the Virtual graphics card the VirtualBox emulates for any guest operatig system provides all the basic features, the custom video drivers that are installed with the Guest Additions Provide you with extra high and non-standard video modes as well as accelerated video performance."

cosbear

---

### Post by eentonig on 2007-06-04
VMWAre I'm used to. And is indeed not that hard to install on Feisty.

But Virtualbox seems to be the vote of the masses by now. So'll have to give that a try apparantly.

---


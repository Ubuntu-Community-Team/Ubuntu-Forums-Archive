---
title: "What packages are in the default install?"
date: 2006-10-22
forum: General Help
---

### Post by alecjw on 2006-10-22
Hi. Can anyone give me a complete list of all of the packages whihc you get when you install ubuntu from the desktop cd please? Is it just the ubuntu-desktop package?

I'm going to white a howto on installing ubuntu from a business card cd, minidisk or even a floppy but i need to know hat packages to install.

---

### Post by DaveBorealis on 2006-10-22
> **alecjw said:**
> Hi. Can anyone give me a complete list of all of the packages whihc you get when you install ubuntu from the desktop cd please?

One way to get the list, assuming that you have a freshly installed system, is:

     System -> Administration -> Synaptic Package manager

And then click the 'Status' button and select 'installed'

Best regards,
Dave

---

### Post by az on 2006-10-22
> **alecjw said:**
> Hi. Can anyone give me a complete list of all of the packages whihc you get when you install ubuntu from the desktop cd please? Is it just the ubuntu-desktop package?

I'm going to white a howto on installing ubuntu from a business card cd, minidisk or even a floppy but i need to know hat packages to install.

If you install just a base system, you can pull in the whole default desktop system by installing the ubuntu-desktop package.  That will pull in all of the dependencies for you.

Are you going to make an iso of the base system?

---

### Post by alecjw on 2006-10-22
> **azz said:**
> If you install just a base system, you can pull in the whole default desktop system by installing the ubuntu-desktop package.  That will pull in all of the dependencies for you.

Are you going to make an iso of the base system?

I'm gonna install debian from a netinst floppy and edit the sources.list to the ubuntu repos, sudo aptitude upadte, sudo aptitude dist-upgrade, sudo aptitude install (k/x)ubuntu-desktop.

---

### Post by az on 2006-10-22
> **alecjw said:**
> I'm gonna install debian from a netinst floppy and edit the sources.list to the ubuntu repos, sudo aptitude upadte, sudo aptitude dist-upgrade, sudo aptitude install (k/x)ubuntu-desktop.

It may work.   It may not.  It depends what release of Ubuntu and what release of Debian you use.  Debian and Ubuntu are not binary-compatible, you know.

---

### Post by ice60 on 2006-10-22
this might help. i haven't read it though, i just had it bookmarked.
[http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

---

### Post by skymt on 2006-10-22
There are lots of alternative ways to install Ubuntu. See the [Installation page](https://help.ubuntu.com/community/Installation) on the Wiki. A couple of my favorites are [from a USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick) and [from another machine on a LAN](https://help.ubuntu.com/community/Installation/LocalNet). [From floppies](https://help.ubuntu.com/community/Installation/WithFloppies) is also included.

---


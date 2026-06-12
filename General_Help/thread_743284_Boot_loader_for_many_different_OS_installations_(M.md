---
title: "Boot loader for many different OS installations? (Mac OS X, Windows, and Ubuntu)"
date: 2008-04-02
forum: General Help
---

### Post by Guy Gizmo on 2008-04-02
I'm running a Mac Pro with two hard drives, one formated using the GUID Partition Map and one using a MBR Partition Map, with six different operating systems installed between the two of them: two versions of Mac OS X, two installations of Windows, and two installations of Ubuntu.

I'm trying to set up a boot loader to elegantly handle all of this, but I'm not sure what to use, or even how to configure it.  Right now I  have rEFIt installed to let me pick a Mac OS X installation, and grub for when rEFIt / bootcamp boots the computer in Legacy mode.

I've tried configuring rEFIt to handle everything, but it has several problems:
1. It lists every single hard drive partition, regardless if there's an OS on it.  There are so many icons they loop off screen and wrap around on top of themselves, and it's very difficult to select anything.
2. Selecting a Windows or Ubuntu partition all do the same thing as picking the 'Legacy' option: it boots to the grub boot loader.

If I want to boot to Windows, I have to select 'Legacy' in rEFIt, then pick 'Windows NT/2000/XP' in grub, and then pick the right Windows install in the Windows NT boot loader.  That's three different menus, and not a very good way of doing things.


So, is there a boot loader I can use to handle this more effectively?  Ideally, I'd like just one boot menu that lets me pick any of these six OSes I want.  If that's not possible, a setup where I use rEFIt / bootcamp to pick between Mac OS X or legacy mode, and then use a second boot menu to select any of the Linux or Windows installations would be good too (though because of the icon problem in rEFIt it would be nice to avoid that).

However, I have no idea how to set this up or which boot loader would work best.  Can anyone help me out?

---

### Post by dannyboy79 on 2008-04-02
you might find your answer here thar grub can do it.

[http://wiki.osx86project.org/wiki/index.php/Quad_booting](http://wiki.osx86project.org/wiki/index.php/Quad_booting)

---

### Post by Guy Gizmo on 2008-04-02
> **dannyboy79 said:**
> you might find your answer here thar grub can do it.

[http://wiki.osx86project.org/wiki/index.php/Quad_booting](http://wiki.osx86project.org/wiki/index.php/Quad_booting)
That article is a little enlightening, but there's a few things about it I'm not sure about.  One is that it seems to be meant for PCs booting using BIOS, and my Mac Pro uses EFI, so I can't use grub as my primary boot loader.  Secondly, it looks like it only works for one version of Mac OS X (and it's unclear if it'll work with the official versions of Mac OS X, as it's meant for OSx86.)

---

### Post by Guy Gizmo on 2008-04-02
After doing some more research, it looks like there is no bootloader that can handle Mac OS X, Linux, and Windows all at the same time, except for rEFIt, and I can't get rEFIt to let me pick specific OSes that aren't Mac OS X.

So, on to plan B: how can I configure grub to boot individual Windows installations, as well as Linux?  Right now, everytime I pick a Windows partition from the grub bootloader, it goes to the Windows NT bootloader, but I don't want it to do that - I just want it to boot Windows.

---

### Post by Guy Gizmo on 2008-04-03
Can anyone help me with this?  I'm no closer now to solving it on my own than before.

(Basically I need help getting grub to load specific windows installations.)

---


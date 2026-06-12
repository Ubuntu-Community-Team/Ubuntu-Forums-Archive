---
title: "Remote Control That Works With Grub And Would Allow Me To Choose Which OS To Boot"
date: 2007-12-10
forum: General Help
---

### Post by pun on 2007-12-10
would any remote control work with grub and allow me to choose which OS to boot if not are there any guides to get it working please help looking to get a SoundGraph iMON VFD which would allow me to turn on the pc with a remote but would i be able to control grub with it

[http://www.soundgraph.com/Eng_/Products/imon25.aspx](http://www.soundgraph.com/Eng_/Products/imon25.aspx)

---

### Post by barney_1 on 2007-12-10
First off, do you really need to control Grub with a remote control?  Do you intend to frequently select a different OS as startup?  If not, you should just be able to set the default OS in grub so that it will automatically boot to that unless you use a keyboard to override it.

Secondly, no, I don't believe that remote will be able to control grub.  The only way I can see a remote control working with grub is if it plugs in and recognizes as an actual keyboard (either PS2 or USB but it has to be recognized by bios as a keyboard either way).  This is because there are no drivers for other peripherals running when grub asks you to select an OS.

---

### Post by pun on 2007-12-11
so no, how about commercial or open source software that would support remotes or emulate the drivers needed

---

### Post by mozetti on 2007-12-11
The problem is that GRUB runs before Linux runs, so the BIOS would have to recognize and be able to use the remote. As **barney_1** said, the remote would have to be recognized as either a keyboard or mouse by the BIOS. I don't know anything about remotes, so I'm not sure if that functinality even exists.

---

### Post by eriqjaffe on 2007-12-11
I just use a wireless keyboard, myself.  It's kind of big for a remote, but at least I don't have to worry about compatibility.  ;)

---

### Post by barney_1 on 2007-12-11
Yes, a wireless keyboard or wireless mouse would do the trick.

---

### Post by zach12 on 2007-12-11
GRUB loads ubuntu

---

### Post by Xbehave on 2007-12-11
all solutions would be hardware bassed keyboard input, as AFAIK thats all that grub can handel,

alternatively if your could go for a complex setup using a minimal kernel to chainload anything you want,
or switch the grub default then reboot then the os would then have to be setup to restore the default grub (alot easier than it sounds if you can get the kernel working to accept keyboard input its just a series of mv scripts or if your really cleaver patch scripts)

---


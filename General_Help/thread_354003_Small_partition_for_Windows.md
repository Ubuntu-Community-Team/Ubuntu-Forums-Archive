---
title: "Small partition for Windows"
date: 2007-02-05
forum: General Help
---

### Post by Anonii on 2007-02-05
Greetings there.
I have to create a poster for a school festival, and I'm wondering if I can resize one of the existing partitions and install Windows XP in it. I just want 1GB for Photoshop, and I'll probably delete the partition after the work is done. Is there a fast and "safe" way doing this?
EDIT: I've heard there is Vmware and such applications that allow you to emulate Windows. Do they run well (well as fast and stable)? Can someone give me a guide which I could use?

Thanks.

---

### Post by MiCovran on 2007-02-05
You don't need photoshop for a poster. I'm sure GIMP will do just fine for you. It can work with .psd format if you need to use photoshop files.

If you just want to install windows, you can resize partitions using the gparted (it's in ubuntu repositories).
Be carefull: when you install windows, it will mess up your MBR and you'll have to restore GRUB (this could help: [http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)).

I don't know about windows emulations, maybe someone else can help you.

---

### Post by Ryan450 on 2007-02-05
VM ware is certainly an option, also a program called Wine can be installed to try and allow the program to run under linux, although it can run various programs pretty buggy I've found. However there is a large number of apps that run flawlessly under it. 

If you decide to install windows xp into a small partition you can resize to allow the space, just keep in mind that windows will overwrite your grub boot loader in the process, which can be recovered using the livecd. 

if you deicde to try wine go here first to see how others have reported the program in question runs under it. 

[http://appdb.winehq.org/](http://appdb.winehq.org/)

however if its just for creating an image, then try your hand at the GIMP. It has all the options that photoshop, but the means of getting to the end result are quite different.

---

### Post by etank on 2007-02-05
I agree with the other posters that the gimp should be able to do what you are needing. If you want to use something like VMware then may I suggest VirtualBox? It runs very well and is easy to install and use. You can find it a [http://virtualbox.org](http://virtualbox.org)

---


---
title: "running xgl and compiz in edgy."
date: 2006-12-21
forum: General Help
---

### Post by cptjaben on 2006-12-21
I'm wondering what experiences people have had running Xgl/compiz on edgy. I know it was a bit of a rocky install in Dapper and as edgy has had difficulty running stably for me I'm wondering what experiences people have had installing it. Thanks

---

### Post by shanepardue on 2006-12-22
I would say you're better off with Beryl, but that's my opinion based on my experiences. Is AIGLX 
out of the question?

---

### Post by cptjaben on 2006-12-23
I can't say that I've really been up on the xgl/compiz scene lately. What exactly is beryl and AIGLX

---

### Post by blackmh on 2006-12-23
Beryl is fork of compiz. If you have Nvidia, installation is a matter of adding repositories and adding couple of lines to xorg.conf.. 

[http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by cptjaben on 2006-12-23
I have an ATI radeon 9700, what would be the best choice?

---

### Post by littlespy on 2006-12-25
> **cptjaben said:**
> I have an ATI radeon 9700, what would be the best choice?

somone can correct me if im wrong but i don't think aiglx will work on an ati card i'd say your best bet is to go with xgl/compiz

i personally tried both compiz and beryl and has more success with compiz than the fork

---

### Post by ramjet_1953 on 2006-12-25
Hi, Guys!

I have the Intel 915 Chipset, and Edgy, so all I had to do was to install Beryl.
I followed the guide on the Berly WIKI site and all went well.
Can't get the water effects to work, though.

Regards,
Roger 8)

---

### Post by raul_ on 2007-01-03
I'm busting my head to get Compiz to work in Edgy with fglrx drives. It seems i'm the only one trying to install it...ever! No how-to's, no posts, compiz forums down...geezz

---

### Post by jlc on 2007-01-03
> **raul_ said:**
> I'm busting my head to get Compiz to work in Edgy with fglrx drives. It seems i'm the only one trying to install it...ever! No how-to's, no posts, compiz forums down...geezz

Why not beryl instead of compiz?

---

### Post by raul_ on 2007-01-03
I had Beryl. I'm trying to get compiz because i heard it runs more smoothly. and since i can't get it installed, it's just one more reason to keep trying :D i guess i'm just stubborn

---

### Post by strawman on 2007-01-10
you can use an ati with aiglx but it requires the open source ati or radeon driver not fglrx.

i'm running edgy with radeon driver, aiglx and beryl; works well.  the only issue for me is that when the laptop resumes from suspend during a beryl session the desktop and open windows are incorrectly rendered and i have to restart beryl-manager.

i seem to recall when i tried compiz with xgl and fglrx that everything resumed properly.

incidentally, when using the ati or radeon driver  for my mobility 9600, i had to delete the splash option in /boot/grub/menu.lst ( in addition to editing /etc/default/acpi-support) in order to get suspend to ram working.  when using the fglrx driver this was not neccesary.

cheers

---


---
title: "MemTotal:       906660 kB"
date: 2005-10-21
forum: General Help
---

### Post by Gowator on 2005-10-21
I have tried changing kernel's to the K-7 kernel (on an AMD 64) so I can get the other half of my memory back but everytime I change the nvidia driver locks up.  

I tried the one in restricted and recompiling from the nvidia download with the same result.  

I don't want to have to compile my own kernel since then I will end up with lots of dep problems in the Ubuntu sources...

I'm currently running Hoary so would moving to Badger fix this problem or is this a deliberate restriction on Ubuntu in which case Ill just go back to pure Debian?

---

### Post by Gowator on 2005-10-23
Ah, I remember.. this forum is just for asking questions like how do I send a document to the trash can.

... any technical question will of course go unanswered ...
I really don't know why you bother.. these forums are about as crap as any I have seen for actually finding an answer to anything.  

Does anyone on these forums actually use Ubuntu ?

---

### Post by RAOF on 2005-10-23
Ok, I'll bite.  Presumably, you've got 2gb of ram, and the kernel's only seeing the bottom gig, yes?  Now, IIRC, there's a boot parameter you can pass to the kernel to get it to recognise more memory.  In fact, looking at man bootparam, it seems that adding the "mem=whatever" option might be what you're after.

For your other problems... when you say "the nvidia driver locks up" what, exactly, do you mean?  The computer freezes?  X fails to start?  Are there any error messages, kernel panics, xorg logs you could provide?  Have you tried the "nv" driver, and does that work?  One of the possible reasons you haven't got a response is that you haven't actually described your problem at all, which makes it really difficult to help you.

It's actually quite easy to compile your own kernel the ubuntu way, which ends up with the kernel image and everything else installed via apt, so it's easy to remove.  The howto's [here]("https://wiki.ubuntu.com/KernelHowto").  I've just followed that in an (unsuccessful) attempt to get my DVB card working, and it's pretty straightforward, and doesn't break anything except the nvidia driver, which I had to install the kernel module using the nvidia installer.

---

### Post by Gowator on 2005-11-01
[QUOTE=RAOF]Ok, I'll bite.  Presumably, you've got 2gb of ram, and the kernel's only seeing the bottom gig, yes?  Now, IIRC, there's a boot parameter you can pass to the kernel to get it to recognise more memory.  In fact, looking at man bootparam, it seems that adding the "mem=whatever" option might be what you're after.

For your other problems... when you say "the nvidia driver locks up" what, exactly, do you mean?  The computer freezes?  X fails to start?  Are there any error messages, kernel panics, xorg logs you could provide?  Have you tried the "nv" driver, and does that work?  One of the possible reasons you haven't got a response is that you haven't actually described your problem at all, which makes it really difficult to help you.

It's actually quite easy to compile your own kernel the ubuntu way, which ends up with the kernel image and everything else installed via apt, so it's easy to remove.  The howto's [here]("https://wiki.ubuntu.com/KernelHowto").  I've just followed that in an (unsuccessful) attempt to get my DVB card working, and it's pretty straightforward, and doesn't break anything except the nvidia driver, which I had to install the kernel module using the nvidia installer.[/QUOTE]

X just freezes with the nvidia driver.  
nv works fine...  except I can't use my second screen (projector)as a seperate X server which I need to do not use Xinerama

The problem with doing your own kernel is you end up in endless traps...
Ive been doing this to myself sionce RH5.1 and its always the same thing.. you add support for item X ... and everything is cool to you wanna upgrade .. then everything is broken until you fix your new kernel..or upgrade somethig with a library dep which needs a newer kernel or another patch  its not a big deal once off but doing it all the time gets tiresome..which is why I wanna use a binary distro as a desktop...my server runs gentoo with kernel 2.4 still!  

I chanced an upgrade to the 2.6.12-9-386 which actually does support 4GB mem - so it worked out OK ...

---

### Post by jeremy on 2005-11-01
[QUOTE=Gowator]... any technical question will of course go unanswered ...
I really don't know why you bother.. these forums are about as crap as any I have seen for actually finding an answer to anything. [/QUOTE]
Do please enlighten us when you find a better forum.

---

### Post by Gowator on 2005-11-02
[QUOTE=jeremy]Do please enlighten us when you find a better forum.[/QUOTE]
How hard is it...

I haven't had a single Ubuntu specific question answered here. 
Nowhere else can you go a month or more on 3 or so critical issues without any answer whatsoever!!!!!

---


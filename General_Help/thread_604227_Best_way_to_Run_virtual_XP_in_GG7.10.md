---
title: "Best way to Run virtual XP in GG7.10?"
date: 2007-11-05
forum: General Help
---

### Post by bill45 on 2007-11-05
Any suggestions or experience runing XP as a VM in 7.10? I have some multi-media scheduling recording software that only runs in WinXP.  Is all necessary VM software available from Synaptic or Add/Remove? 

Thanks
Bill C

---

### Post by JoskeBangelijk on 2007-11-06
I recently switched from vmplayer to virtualbox. Virtualbox is the best, and so easy to set up, you'll be running windows in less than two hours.
Best of all: it's free software!
Don't forget to install the so-called "Guest additions". They will give you the ability to mount a drive on your windows system, change the windows resolution if you change the windows size, and automatically grab and release the mouse when you move over the window.
And it's fast, fast, fast, if you switch to fullscreen mode, you won't notice that you are not behind a windows machine.

So: virtualbox, virtualbox, virtualbox!!!

---

### Post by Nesmontu on 2007-11-06
KVM+Qemu is very fast too. As for virtualbox, there's a great guide on how to set it up with XP [here]("http://ubuntuforums.org/showthread.php?t=433359"). For KVM+Qemu, there's a guide on the Ubuntu wiki, just do a search for KVM :)

---

### Post by Gullie on 2008-03-01
> **JoskeBangelijk said:**
> I recently switched from vmplayer to virtualbox. Virtualbox is the best, and so easy to set up, you'll be running windows in less than two hours.
Best of all: it's free software!
Don't forget to install the so-called "Guest additions". They will give you the ability to mount a drive on your windows system, change the windows resolution if you change the windows size, and automatically grab and release the mouse when you move over the window.
And it's fast, fast, fast, if you switch to fullscreen mode, you won't notice that you are not behind a windows machine.

So: virtualbox, virtualbox, virtualbox!!!

Nonsens. When using VB you are installing a normal Windows OS with all it's crap.

---

### Post by tshearman on 2008-03-01
I'm trying this setup now; however, I'm having issues with the Guest Additions.

I go "Devices > Install Guest Additions" and wait... but nothing

Seen this before?
thanks

---


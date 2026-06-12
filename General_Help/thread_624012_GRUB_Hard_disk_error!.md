---
title: "GRUB Hard disk error!"
date: 2007-11-26
forum: General Help
---

### Post by leat on 2007-11-26
Hi, im new with this whole ubuntu-stuff, so please be a little bit patient :P

Anyways, I've installed Ubuntu like 20 times but I still get the same error when trying to boot from Harddrive.

I've tried every help thread I've seen, and that's alot.

But I think the problem is that when Im looking for the drive/partition (only have 1 drive) where GRUB is located on. I get hd0,0. now when I try to setup (hd0,0) it says that stage 1.5 failed, and that's the error I get when im trying to boot. 

Now when I try to install it on hd0, everything says its ok, embedded, done and such. but I still get the same error when booting from harddrive.

Does anyone have a real way to FIX this? or do I have to go back to Windows?

Thanks, Pierre

---

### Post by ZipoTe on 2007-11-26
And the error mesage is?...

---

### Post by leat on 2007-11-26
"GRUB Loading Stage1.5
GRUB Hard Disk Error"

---

### Post by ZipoTe on 2007-11-26
It doesn't print any error number?, just like

Error <num>

---

### Post by leat on 2007-11-26
No, it does not :S

---

### Post by leat on 2007-11-27
help please?

---

### Post by teryowen on 2007-11-27
instead go to terminal type this:

grub
root (hd0,0)
setup (hd0)
quit

---

### Post by teryowen on 2007-11-27
Any luck?

---

### Post by leat on 2007-11-27
nothing happens when I write root (hd0,0) nor root (hd0)

---

### Post by teryowen on 2007-11-27
did u write

root (hd0,0)

not just root?

---

### Post by leat on 2007-11-27
I wrote root (hd0,0)

---

### Post by teryowen on 2007-11-27
Are you in the grub input, type thing?

---

### Post by leat on 2007-11-27
yes, sudo grub before the other commands

---

### Post by teryowen on 2007-11-27
is your hard drive reckognized by the BIOS?

Either way i guess this isnt working to well, perhaps you should try super grub, go and download it and see how that works out for you many people have suggested that personally ive never used it though.

---

### Post by leat on 2007-11-27
well, my BIOS aint detecting my HD cuz it's S-ATA, maybe if I put linux on an IDE-hd instead?!

---

### Post by teryowen on 2007-11-27
Well theres your problem, ive never really had problems with hard drive detection so i dont know exactly how to fix it,

but make sure your BIOS/computer sees the hard drive and then you will be able to install GRUB.

But if you can see your ubuntu partition which is installed on the hard drive while running of the Live CD then there is no problem with the hard drive. In which case im at a dead end and i dont know what to do for you. Best of luck.

---

### Post by leat on 2007-11-27
Ok i'll try! Thanks alot!

---


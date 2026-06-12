---
title: "[SOLVED] transferring files to virtualbox?"
date: 2008-06-01
forum: General Help
---

### Post by crazyfuturamanoob on 2008-06-01
I have ubuntu on hard disk, and windows on virtualbox.
I want to play windows games with that windows, but it
needs directx update. How do I transfer files to the
virtual hard drive inside virtualbox?

I have a good reason that I don't want to tell you to
not have network connection on my windows.

---

### Post by ibuclaw on 2008-06-01
You can burn all the install files into an iso image file.
Then mount the iso in your VirtualBox settings before you boot it up.

Once booted in, either run them off the virtual CD, or copy them straight in to your virtual drive.

Regards
Iain

---

### Post by crazyfuturamanoob on 2008-06-01
> **tinivole said:**
> You can burn all the install files into an iso image file.
Then mount the iso in your VirtualBox settings before you boot it up.

Once booted in, either run them off the virtual CD, or copy them straight in.

Regards
Iain
That's what I thought too, but I can't find software
that would pack files to .iso or similar files.

---

### Post by ibuclaw on 2008-06-01
> **crazyfuturamanoob said:**
> That's what I thought too, but I can't find software
that would pack files to .iso or similar files.

Brasero has that option.

I think that it is right before you confirm the Burning, there should be a dropdown tab that lets you choose between "CD-R" and "Image file".

[EDIT]
Also, there is the command mkisofs:

ie:
```
mkisofs -J -r -o MYINSTALLS.iso **FOLDER**
```

Regards
Iain

---

### Post by crazyfuturamanoob on 2008-06-01
Thanks it works, wohoo Dark Reign 2 rules!

---

### Post by niteshifter on 2008-06-01
Hi,

Install the VB GuestAdditions and then set up sharing. However ....

If those games need DirectX w/ 3D support: Won't work.

If you're running Ubuntu with Windows on a 256MB RAM machine, you're going to be disappointed with both OSes - not enough RAM.

---

### Post by crazyfuturamanoob on 2008-06-01
Oh, that info in my sig is only about my other computer.
This one using virtualbox has ~1gb ram.

---

### Post by Kain000 on 2008-12-26
how about if you just wanted to transfer music files to a virtural c drive?

I cannot find it in nautlus and I am wanting to use the itunes store to put videos on my ipod as I cannot figure it out with gtkpod.

---


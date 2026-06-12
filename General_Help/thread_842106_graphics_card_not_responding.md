---
title: "graphics card not responding??"
date: 2008-06-27
forum: General Help
---

### Post by napolean9 on 2008-06-27
hi so apparently my computer isn't reading my graphics card. when i boot up it says that there is no graphics card and so i will have to change my resolution to 800x600. once i log in, it checked my driver and it's the latest and enabled. i went to system > hardware testing and the video test failed. i went to system > NVIDIA X server settings and it says:

 "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

any ideas? i would post more information but i'm not sure what else i should post.

---

### Post by iaculallad on 2008-06-27
On your terminal:

```
lspci | grep VGA
```

Try to post the output.

---

### Post by napolean9 on 2008-06-27
here's the output:

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by napolean9 on 2008-06-27
bump

---

### Post by jimbob on 2008-06-27
I have the same problem .  It started when I upgraded to kernel 2.6.24-19-generic from 2.6.24-18-generic.  The latter one still works fine.  All of the nvidia-glx stuff is in place as well as a new linux-restricted-modules file for 2.6.24-19.  What could be causing this?

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

---

### Post by jimbob on 2008-06-27
Here is a fix that worked for me.  Boot up your system in whatever mode it starts in (mine was using 640x480, UGH!) and install envyng-core and envyng-glx.  Start envyng-glx in a terminal as root, click on Nvidia and apply and let it do its thing.  Mine deleted nvidia-glx-new and nvidia-settings and then installed (re-installed?) a bunch of stuff and asked me to reboot which I did and voila! - worked like a charm.

---

### Post by napolean9 on 2008-06-27
thanks i'm trying that out right now

---

### Post by napolean9 on 2008-06-27
ya nothing changed, this is becoming really frustrating.
i wonder if it's just something wrong with my motherboard? i know the driver is installed and enabled, so what else could it be?

---

### Post by jimbob on 2008-06-28
Did this happen when you went from 2.6.24-18 kernel to 2.6.24-19 like mine did?  Did you try loading the old kernel?

I think your card is recognized or you wouldn't have the output from lspci that you did.

---

### Post by napolean9 on 2008-06-28
it didn't start as soon as i went to the new kernel, but pretty soon after if i recall correctly. 

I might as well check anyway, how do i load an old kernel?

---

### Post by jimbob on 2008-06-29
The quick way just to try it would be to edit the grub menu when it first comes up.  Follow the instructions at the bottom of the menu.  Just change the 19 to 18 in both the kernel and initram lines and hit b to boot.

---


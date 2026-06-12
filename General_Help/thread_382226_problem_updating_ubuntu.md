---
title: "problem updating ubuntu"
date: 2007-03-11
forum: General Help
---

### Post by oktob3r on 2007-03-11
well i just installed unbuntu and i went to install the updates after they all downloaded it froze, i tried to restart and in grub it was ubuntu 10.0.2 or something like that i tried to go into it and it said it has a kernal error or something but i could still get into 10.0.1 any way to fix this? or should i be worried?

sorry i'm a complete ubuntu n00b

unrelated but problem as well when i go to do something in terminal i get this error message

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

---

### Post by HereInOz on 2007-03-11
It is a bit hard with the information that you have given, but it sounds like there has been an upgrade of your Linux kernel and that is either corrupt or it is causing a problem with something like your video card, or similar.

I would not be immediately concerned if you need to go in to a previous kernel to get the system to boot, but, of course, it does need fixing in the longer term.

I suppose that you could always run the install again, but I reckon that there is a way that you can make apt download the newer kernel again and install it, but tragically that is beyond me.   

What would I do?  Given that it is a new installation, I would reinstall from scratch again, and see if it happens the same again, and if that is the case, then there is possibly an issue with some hardware that the new kernel does not like.

---

### Post by HereInOz on 2007-03-11
That error message is related.

Open a terminal, and type in

sudo dpkg --configure -a  (are you sure this is it, and not dpkg-configure -a ?   If one doesn't work, try the other.)

and then type your password.

That may get you out of the hole you are in.

---

### Post by HereInOz on 2007-03-11
I was wrong - it is dpkg --configure -a.

Sorry about that.

---

### Post by oktob3r on 2007-03-11
well first let me say thank you both for the fast response, i tried to fix it using a code which someone posted having a similar problem in a different thread and it worked, i had to restart and i belive it worked fine now because it didn't give me any error. i do have another question (sorry i'm sure they will keep comming)

trying to use digikam to upload photo's is giving me this error


"An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device."

---

### Post by llamakc on 2007-03-11
The proper thing to do is start a new thread, after you have searched the forums for an answer.

---

### Post by HereInOz on 2007-03-11
Dead right.  You should start a new thread.

A hint though, that issue is not unknown, so search the forums for the error message and you may come up with something.

It happens with other digital cameras as well.

---

### Post by oktob3r on 2007-03-11
sorry i will from now on... just didn't want to flood the place that's all

---


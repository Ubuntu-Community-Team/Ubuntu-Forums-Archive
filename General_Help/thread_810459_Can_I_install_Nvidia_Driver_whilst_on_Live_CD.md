---
title: "Can I install Nvidia Driver whilst on Live CD?"
date: 2008-05-28
forum: General Help
---

### Post by md152 on 2008-05-28
Hey um just trying to get Desktop effects to work but i think i need the driver. SO i downloaded the right one for my card and x32 Ubuntu, but i do not know how to install it. Is it possible? Thanks

EDIT

I figured out how to install it but it said it needed to be run from the root file.
Is it saying that because im running off Live CD?

---

### Post by tanzoniteblack on 2008-05-28
You should be able to install the nvidia driver that's in the repositories while on the live CD.  I'm assuming you're using Hardy Heron (8.04), but Gutsy Gibbon (7.10) should be the same.  Go to System --> administration --> Software Sources and make sure that the restricted drivers are turned on. Now go to Synaptic package manager (right under software sources) and install nvidia-glx (if you're using an older card nvidia-glx-legacy will be needed instead...check on the nvidia website to know which to use if you're unsure).

Once it's installed instead of restarting the computer, as you would do to finish installing this if you had it on your harddrive (though if you did it then you wouldn't needed to go through those steps as the Ubuntu restricted driver's manager will help you install it the first time you turned it on), you instead need to restart the X server by pressing ctrl+alt+backspace.  This will close all programs and log you back in, hopefully with the nvidia driver loaded so you can use the desktop effects.  Good luck!

To answer your question about the root file thing, when you install the driver from the website you have to be root (or super) user.  If you actually wanted to install it that way you'd have to do "sudo sh <nvidiadriver>.sh" to run it, the sudo command is what allows you to run anything in a terminal as root.  However, the graphical method should be easier.

---

### Post by FuturePilot on 2008-05-28
It won't work from the live CD. I've tried it a number of times before and it just fails. Especially since they have updated Hardy's kernel to -17. If you try to install it from the live CD it will download the driver compiled against the -17 kernel while you are using the -16 kernel on the live CD. This will just fail.

---


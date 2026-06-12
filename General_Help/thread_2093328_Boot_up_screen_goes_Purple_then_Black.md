---
title: "Boot up screen goes Purple then Black?"
date: 2012-12-10
forum: General Help
---

### Post by SavagedenutsxX on 2012-12-10
Hi Guys, I'm fairly new to Ubuntu (and Linux in general) and I am trying to install Ubuntu on my dads old Acer laptop. I luckily haven't given up, so I am asking here. I installed Wubi just for saftey reasons, because if something went wrong like so, then I go on my Windows for this.

So, when I boot up, Win8 tells me to choose Win8 or Ubuntu, so I choose Ubuntu, it tells me my processor on the right before the boot up menu. My specs are in the image below (or from the Control Panel, anywho).

[IMG]http://i.imgur.com/bWJX8.png[/IMG]

So, I also cant seem to type anything as it goes to fast, and the purple screen is just purple, nothing else. I would love it if you could help me, and I will hopefully be able to pay you back sometime.

I wanted to install Linux for practice w/ coding e.t.c which I am getting ready for a college course. Thanks for reading :popcorn:

---

### Post by bcbc on 2012-12-10
What graphics card do you have? Probably it needs a custom driver (if it's nvidia or radeon).

So, do this... select Ubuntu and then hold down the Shift key immediately. This should pop the grub menu. Then select Advanced options, and then the second entry (Recovery mode). Then you'll get a menu from which you can select "Resume normal boot".

Now you're booting with `nomodeset` (a workaround for unsupported graphics cards). See if you can install a custom graphics driver - it should prompt you - or you can run 'additional-drivers'.

---

### Post by SavagedenutsxX on 2012-12-10
You are a god amongst men, I actually have it working and now I'm learning the features and installing my software. Thanks dude, you saved a lot of time for me. 

This is now solved.

---

### Post by bcbc on 2012-12-10
You're welcome! 

"You are a god amongst men": awesome, thanks for the good chuckle.

---


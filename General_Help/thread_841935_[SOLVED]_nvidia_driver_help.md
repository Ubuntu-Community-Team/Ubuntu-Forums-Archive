---
title: "[SOLVED] nvidia driver help"
date: 2008-06-26
forum: General Help
---

### Post by cheesypoof on 2008-06-26
I have an 8800gts and a viewsonic a90f+. I originally installed the nvidia drivers(169.12) through the add/remove program. I used them for quite a while and they worked out fine. I noticed that the nvidia site had newer ones(173.14.09), so I proceeded to uninstall my old ones and try to install the new ones from the nvidia site. After restarting, it was forced to 800x600 unfortunately. After setting the terminal to my desktop, I typed "sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run". It said I had X running, so then I googled how to stop x(/etc/init.d/gdm stop) without realizing that it would literally put me to a black screen with random text. I then restarted and my monitor was displaying everything all stretched out which made the details indistinguishable, so I couldn't navigate anywhere visually. My question is, what do I do from here. How do I either reinstall my old drivers or continue with the install of the new ones. Oh and btw, I can't even select a different session at the login screen because I can't see the button.

---

### Post by sdennie on 2008-06-26
Assuming you can get to a terminal (Ctrl-Alt-F1 should do it) you should be able to get the old drivers back using:

```

sudo apt-get install nvidia-glx-new

```

If you want to try the new drivers, try this guide: [http://ubuntuforums.org/showthread.php?t=797270&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=797270&highlight=nvidia)

---

### Post by cheesypoof on 2008-06-26
I was feeling quite hopeless for a moment. Thanks so much, your link helped me to successfully install the new drivers. :) If only I would have thought about using the recovery mode before I posted this....

---


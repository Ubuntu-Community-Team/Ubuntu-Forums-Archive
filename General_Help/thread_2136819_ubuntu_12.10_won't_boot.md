---
title: "ubuntu 12.10 won't boot"
date: 2013-04-18
forum: General Help
---

### Post by ulmon on 2013-04-18
As the title says, I can't boot into my ubuntu partition.  See video for what is happening. 
[http://www.youtube.com/watch?v=_KL2kiK-URo&feature=youtu.be](http://www.youtube.com/watch?v=_KL2kiK-URo&feature=youtu.be)

Some additional info.
My system is running a radeon 7970 and intel 3770k.  It is also configured to go into a gnome3 desktop by default.  My windows partition works fine.

I am really stumped and can't think of any options besides reinstalling the OS, which is not ideal.  The drive is ok because I've mounted it in a Live CD and can browse the files correctly.  

Thank you for any help you can offer and let me know what kind of information you need in order to provide assistance.

Edit: Got it fixed by uninstalling my graphics drivers from the recovery terminal and re-installing once I got in.

---

### Post by dgharmon on 2013-04-20
Says 'this video is private' ...

---

### Post by yekin on 2013-04-20
Probably you have installed windows after installing ubuntu.

I think reinstalling GRUB will solve your problem. You can read [here]("https://help.ubuntu.com/community/Grub2"). Find out how to reinstall grub.
Follow the link in the [Installing/Reinstalling/Moving GRUB2]("https://help.ubuntu.com/community/Grub2#Installing.2BAC8-Reinstalling.2BAC8-Moving_GRUB2")

---


---
title: "Composite on affects video playing"
date: 2008-05-15
forum: General Help
---

### Post by ELMOesDIOS on 2008-05-15
Hi all!

I like the effects brought by enable composite, but when I turn it on, the video playing is not solid. When the image is quiet, there's no problem but with quickly camera movements, the image loses quality.

It happens with any video player: I test VLC, Mplayer and Totem. I know that is not Compiz because if I turn on the compositing effects of Metacity I have the same problem.

Thank you and sorry for my English, it's poor....

---

### Post by notwen on 2008-05-15
This sounds similar to the issue I was encountering on my Inspiron 1420n.  Try changing the video output to 'No Xv'.  

Which video card are you using?  I'm betting it is currently blacklisted.

---

### Post by ELMOesDIOS on 2008-05-15
Thanks for reply ! My video card is **Nvidia GeForce 7600GT**. I'm running Ubuntu 8.04 and using the restricted driver downloaded from Nvidia website.

How can I change the output? It's in the xorg.conf file? ... I've been searching for options in players like VLC but still nothing ...

---

### Post by ELMOesDIOS on 2008-05-16
I've changed the video output to 'No Xv' on gstreamer-propierties and test Totem... still nothing. Any ideas ?

Thanks

---

### Post by aroch1 on 2008-05-16
You can change the output plugin in VLC by Settings->Preferences->Video->Output Modules and then checking the "Advanced options" checkbox in the bottom right.  Try experimenting with them til you find one that works for you.

---

### Post by notwen on 2008-05-16
The compositing issue I'm referring to only affects the Intel X3100 chipset as far as I know.  You may wish to change your vidoe output back to it's default and look for other possible solutions.  Best of luck.  =]

---

### Post by ELMOesDIOS on 2008-05-16
Thanks everybody for your replies. I change back the video output when I check that it doesn't work. I've tried all the Output Modules in VLC settings but always the same problem happens or the output doesn't work.

I think that if no one has my problem it could be any option that fixes it at the xorg.conf file.

---


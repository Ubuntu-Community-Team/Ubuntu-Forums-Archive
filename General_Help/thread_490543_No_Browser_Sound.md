---
title: "No Browser Sound"
date: 2007-07-02
forum: General Help
---

### Post by Snoo on 2007-07-02
Hi I've trawled the archives but with no luck.

I can't get anysound via my browser (firefox). Youtube/ myspace whatever. It's all silent.

Sound works fine with songbird (though none of the other programs such as VLC etc strangely).

Can anyone help? Flash issue perhaps?


Thanks.

(Ps. Using Ubuntu Fiesty and Firefox is 2.0.0.4)

---

### Post by loserboy on 2007-07-02
[www.ubuntuguide.org](www.ubuntuguide.org) has a list of stuff you can do
or automatix has worked perfect for me every single time [www.getautomatix.com](www.getautomatix.com)

---

### Post by Snoo on 2007-07-02
Still no joy. Installed swiftfox which is giving various warnings of no sound...

---

### Post by loserboy on 2007-07-02
you tried Automatix and it still didn't work?

---

### Post by Snoo on 2007-07-02
OK. This thread seems to tie up with what I am now getting. I am also using an external sound card rather than the on board.

[http://www.linuxquestions.org/questions/showthread.php?t=154031](http://www.linuxquestions.org/questions/showthread.php?t=154031)


I don't understand how to fix it though. I think that is another release but the symptoms seem the same. Anyone tell me how to check that my SB card is the primary? I get test sounds ok from the tool bar menus.

---

### Post by Snoo on 2007-07-02
> **loserboy said:**
> you tried Automatix and it still didn't work?



I loaded in all the media plug-ins, yes. Plus swiftfox.

---

### Post by Slammer64 on 2007-07-02
Have you tried installing alsa-oss ? There's a howto on [www.ubuntuguide.org](www.ubuntuguide.org) that has worked for me. It's worth a shot.

---

### Post by Edgeworth on 2007-07-02
I've experienced similar volume problems with Cnet TV, Try adjusting the volume slider to anything but the default.

---

### Post by Snoo on 2007-07-02
> **Slammer64 said:**
> Have you tried installing alsa-oss ? There's a howto on [www.ubuntuguide.org](www.ubuntuguide.org) that has worked for me. It's worth a shot.

no luck there either sadly.

---

### Post by Snoo on 2007-07-02
Sorted!


$ sudo apt-get install nvidia-glx-dev



did the job for some reason!

---

### Post by loserboy on 2007-07-02
lol, strange but a fix is a fix i guess :)

---


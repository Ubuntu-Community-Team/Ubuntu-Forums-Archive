---
title: "Wrong display mode"
date: 2007-05-17
forum: General Help
---

### Post by pjalegria on 2007-05-17
Hi

I have installed Wubi and everything is ok...but when yhe installation was finished it made a reboot, when Ubuntu star up i have a wrong display mode...and i cant changed because a dont see correctly:(.

In my Windows installation i have 800x600 display mode.
There are any way to change the display mode before Ubuntu starup???

Tank you

---

### Post by heimo on 2007-05-17
Go to virtual console by hitting ctrl+alt+F2. Then use these instructions to reconfigure Xorg (sudo dpkg-reconfigure xserver-xorg):
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Select modes that your monitor / graphics card supports. Another option is to manually edit xorg.conf and remove any unsupported resolutions.

---

### Post by pjalegria on 2007-05-17
cant you explain to me better how cant i do that?...i am a newbie...sorry

---

### Post by heimo on 2007-05-17
> **pjalegria said:**
> cant you explain to me better how cant i do that?...i am a newbie...sorry

Hm... Wubi may make this little different. I have never used it, so I'm not sure if my ctrl+alt+F2 advice for changing to command line / virtual console works. You can try that, but if it doesn't work it's because there's something different when using Wubi (I know pretty much nothing about it) and you'll have to get advice from someone who knows this stuff. :)

---

### Post by ago on 2007-05-17
Wubi should not change ctrl+alt+F2 & friends. It behaves like a standard installation.

As for the display is that a Usplash issue or an X issue? Do you see the Ubuntu logo with the progressabar? Does the progressbar fill up?

---

### Post by pjalegria on 2007-05-17
Yes, i see it.
In the login screen, apear the problem

---

### Post by heimo on 2007-05-17
Try changing to virtual console by hitting ctrl+alt+F2. Log in and type:
```
sudo dpkg-reconfigure xserver-xorg
```

It'll ask a bunch of questions about your system. Select only resolutions / modes that are supported by your display / graphics card.

---

### Post by BikOS on 2007-06-23
Dear all,
I am running into the same problem with the display lousy mode when the X starts and I am facing the GDM. It simply has very clattered vertical lines with colors mostly green vertical lines>
I have tried the manual config to the best I know, to the extend that i have selected a  800*600 mode while am having GF6600.
If there is any other way for it can you let us know.
Did the manual config worked with you  _pjalegria_ ?! 

*Thank you in advance guys, and pardon my English (not native).

_EDIT:_ I meant I have tried the dpkg-reconfigure

---


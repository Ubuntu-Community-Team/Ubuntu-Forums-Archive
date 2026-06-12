---
title: "skype 1.1.0.3 locks awful"
date: 2005-05-19
forum: General Help
---

### Post by kbdcb on 2005-05-19
Hi all,

I have problem with skype both the .deb package and the .bzip2 package. Skype looks real awful, the font is way to big. Is there a way to customize it? Isn't there something called qt-config?

Thanks in advance!

---

### Post by sfw5000 on 2005-05-19
it's designed for KDE, so if you install the kde libs it will look much better.

---

### Post by kbdcb on 2005-05-20
[QUOTE=sfw5000]it's designed for KDE, so if you install the kde libs it will look much better.[/QUOTE]

Is that the only way? What packages do you mean?

---

### Post by sfw5000 on 2005-05-22
Hi,

Sorry for the delay. Yes, I think this is the only way. There are no drawbacks to installing the libs and it should not do anything negative in any way, so it's really a fine solution... trying installing libqt3c102-mt

---

### Post by kbdcb on 2005-05-22
[QUOTE=sfw5000]Hi,

Sorry for the delay. Yes, I think this is the only way. There are no drawbacks to installing the libs and it should not do anything negative in any way, so it's really a fine solution... trying installing libqt3c102-mt[/QUOTE]

Hey,

I tried that but it still looks like this:
[IMG]http://atruth.se/images/skype.png[/IMG]

Isn't there a way to format the text size and fonts in qt?

Cheers.

---

### Post by hanzj on 2005-05-23
Skype on my Ubuntu Hoary looks awful too. The fonts are too big.

---

### Post by ZeroA4 on 2005-05-23
[QUOTE=kbdcb]Hey,

I tried that but it still looks like this:
[IMG]http://atruth.se/images/skype.png[/IMG]

Isn't there a way to format the text size and fonts in qt?

Cheers.[/QUOTE]

You have to install kcontrol (it's on Synaptic) and you have to set a style in kcontrol.

For Example if you want the default Plastik style to apply for Skype. You must change to another style, press apply, change back to Plastik and press apply, all this before starting Skype.

Yeah, Yeah... Qt Sucks!

---

### Post by kbdcb on 2005-05-23
[QUOTE=ZeroA4]You have to install kcontrol (it's on Synaptic) and you have to set a style in kcontrol.

For Example if you want the default Plastik style to apply for Skype. You must change to another style, press apply, change back to Plastik and press apply, all this before starting Skype.

Yeah, Yeah... Qt Sucks![/QUOTE]
 Hey! thanks a lot!

Look a lot better now.

Thank you!

---

### Post by benmoretti on 2005-08-09
[QUOTE=ZeroA4]You have to install kcontrol (it's on Synaptic) and you have to set a style in kcontrol.
[/QUOTE]

what about getting skype to use gtk2?  ](*,)

---

### Post by nocturn on 2005-08-10
About the big fonts, I fixed them like this (for K3B):

go to a terminal, type xdpyinfo |grep reso.
It will output something like 75x75 or 100x100.

Now go to the fonts control panel in gnome, I think you need to click advanced.
There is an option to set the display resolution there, set it to match the above numbers.

This fixed KDE fonts for me without installing KDE control center.

---

### Post by takuzinis on 2005-10-08
Is it possible with kcontrol change the the appearance and all windows in such way they look completely identical to my gnome theme?

---

### Post by sagara on 2007-01-28
> **nocturn said:**
> About the big fonts, I fixed them like this (for K3B):

go to a terminal, type xdpyinfo |grep reso.
It will output something like 75x75 or 100x100.

Now go to the fonts control panel in gnome, I think you need to click advanced.
There is an option to set the display resolution there, set it to match the above numbers.

This fixed KDE fonts for me without installing KDE control center.


Thanks nocturn, this also worked for me!

---


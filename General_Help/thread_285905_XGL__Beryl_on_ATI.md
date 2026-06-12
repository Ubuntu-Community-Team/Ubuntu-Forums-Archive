---
title: "XGL / Beryl on ATI"
date: 2006-10-27
forum: General Help
---

### Post by leetcharmer on 2006-10-27
Can someone point me to a working tutorial to install xgl/beryl on an ati card?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29)

^^^ This ends in error for me when trying to start that XGL session.

---

### Post by boban on 2006-10-27
I used this one (I assume, that you have fglrx intalled): [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

Second tutorial, changed only source.list entries to:

```

deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy main

```
Works perfectly and I can login without Xgl when I need to...

---

### Post by PriceChild on 2006-10-27
Are you running dapper or edgy?

*thread moved*

---

### Post by leetcharmer on 2006-10-27
edgy (like said in the thread tags)

---

### Post by leetcharmer on 2006-10-27
After completing that tutorial in the link you gave me, XGl session loads, but -- the entire session seems to go crazy slow (CPU runs at 100% for Xgl) ... also, my windows no longer have the Ubuntu theme anymore and the minimize, maximize, and close buttons are missing.

If I go to terminal and type in beryl, I get an error:
```
leetcharmer@lappyx64:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

Doing this is what removes the windows options, as well as gnome-panel.

---

### Post by poyner on 2006-10-28
> **leetcharmer said:**
> After completing that tutorial in the link you gave me, XGl session loads, but -- the entire session seems to go crazy slow (CPU runs at 100% for Xgl) ... also, my windows no longer have the Ubuntu theme anymore and the minimize, maximize, and close buttons are missing.

If I go to terminal and type in beryl, I get an error:
```
leetcharmer@lappyx64:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

Doing this is what removes the windows options, as well as gnome-panel.

This is exactly what is happening with me as well. I don't suppose you managed to work out how to fix it? I'm thinking it could be a display 0 or 1 thing but I'm not sure.  Does anyone else have any ideas?

---

### Post by boban on 2006-10-29
> **leetcharmer said:**
> After completing that tutorial in the link you gave me, XGl session loads, but -- the entire session seems to go crazy slow (CPU runs at 100% for Xgl) ... also, my windows no longer have the Ubuntu theme anymore and the minimize, maximize, and close buttons are missing.

If I go to terminal and type in beryl, I get an error:
```
leetcharmer@lappyx64:~$ beryl
XGL Present
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
```

Doing this is what removes the windows options, as well as gnome-panel.

You should run beryl-manager no beryl alone... And there seems to be bug with xgl, sometime I have to press alt+f2 and :

```

killall beryl-manager
beryl-manager

```

Don't know how your gfx card is configured, but perhaps you could try changing display number in /usr/bin/startxgl.sh...

---

### Post by Joe_CoT on 2006-10-31
> **boban said:**
> You should run beryl-manager no beryl alone...

This is contrary to what beryl-manager actually says when you start it up (to run beryl separately), but this worked for me; by choosing to load beryl from the beryl-manager, it worked, instead of just giving me the above mentioned error.

---


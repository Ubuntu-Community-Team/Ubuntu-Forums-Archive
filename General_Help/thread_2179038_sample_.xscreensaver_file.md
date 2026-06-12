---
title: "sample .xscreensaver file"
date: 2013-10-06
forum: General Help
---

### Post by linuxandunix on 2013-10-06
I need to deploy some custom screensaver settings onto a few Ubuntu systems that I manage through puppet configuration management tool.

I was thinking of making a custom .xscreensaver file and pushing it onto these machines.

However, even after installing xscreensaver and running "xscreensaver-demo" and "xscreensaver-command", there is no .xscreensaver file in home directory.

Could someone kindly help me out on this or share a sample .xscreensaver file so that I can edit it?

---

### Post by Anaximander Thales on 2013-10-06
Well, you won't get much help in that.  I was just looking into this as well, as I thought it would be cool to have a custom lockscreen and ran across [a crunchbang post]("http://crunchbang.org/forums/viewtopic.php?id=7907").

XScreensaver has this to say from there [FAQ]("http://www.jwz.org/xscreensaver/faq.html#toolkits"):
**         The unlock dialog is funny looking, why not use GTK?**
     The short answer is, for security reasons.  The unlock dialog       is implemented using raw Xlib because it would be very difficult       to implement it using a GUI toolkit and still have xscreensaver       be secure.  More technical details can be found on the       [On Toolkits]("http://www.jwz.org/xscreensaver/toolkits.html") page.

Most of your themeing for XScreenSaver will occur in the ~/.Xresources and ~/.Xdefaults file.

The initial post I linked to talks about XScreenSaver itself (and is where I get all the information that I'm telling you on this post).

user chillicamparl added this to their .xresource file:

```
! xscreensaver ---------------------------------------------------------------

!font settings
xscreensaver.Dialog.headingFont:        -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
!general dialog box (affects main hostname, username, password text)

xscreensaver.Dialog.foreground:         #ffffff
xscreensaver.Dialog.background:         #000000
xscreensaver.Dialog.topShadowColor:     #000000
xscreensaver.Dialog.bottomShadowColor:  #000000
xscreensaver.Dialog.Button.foreground:  #666666
xscreensaver.Dialog.Button.background:  #ffffff
!username/password input box and date text colour
xscreensaver.Dialog.text.foreground:    #666666
xscreensaver.Dialog.text.background:    #ffffff
xscreensaver.Dialog.internalBorderWidth:24
xscreensaver.Dialog.borderWidth:        20
xscreensaver.Dialog.shadowThickness:    2
!timeout bar (background is actually determined by Dialog.text.background)
xscreensaver.passwd.thermometer.foreground:  #666666
xscreensaver.passwd.thermometer.background:  #000000
xscreensaver.passwd.thermometer.width:       8

```

Hopefully that'll give you some information to start with.

Another person in the post I linked to mentioned Gnome-Screensaver.  This may give you a better platform to modify, but I don't know.

---

### Post by linuxandunix on 2013-10-15
Thanks [**[COLOR=#000000]Anaximander Thales[/COLOR]**]("http://ubuntuforums.org/member.php?u=52350").

---


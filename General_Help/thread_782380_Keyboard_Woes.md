---
title: "Keyboard Woes"
date: 2008-05-04
forum: General Help
---

### Post by rerendered3 on 2008-05-04
In a normal day I find it necessary to switch between keyboards quite often. I had three keyboards enabled and the switcher in the taskbar but recently things have started going crazy. First keyboards started disappearing from the list and now it seems as if only the default is working.

Ideas?

---

### Post by msutton86 on 2008-05-04
First question is wtf are you using three keyboards for?  Second have you checked out your /etc/X11/xorg.conf I think that's where the config.  Should look something similar to this.  I only use one keyboard though.  So I'm not too sure what it'd look like with three.  I assume it would look something like this.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

---

### Post by rerendered3 on 2008-05-05
I work in English, Spanish and Esperanto and one keyboard, especially for Esperanto (&#264;&#284;&#292;&#308;&#348;), just won't cut it. How do multiple layouts look in the config file? The glitch is that 8.40 doesn't save it when it shuts down.

---

### Post by brallan on 2008-09-08
Sorry to bring this fascinating discussion of the merits of Esperanto back to a technical point, but check out the thread below for typing in esperanto using x-sistem, it works as good as Ek!, even allows you to use Dvorak and other latin languages' keyboards (for example french, spanish, turkish, or german)

> **rerendered3 said:**
> I work in English, Spanish and Esperanto and one keyboard, especially for Esperanto (&#264;&#284;&#292;&#308;&#348;), just won't cut it. How do multiple layouts look in the config file? The glitch is that 8.04 doesn't save it when it shuts down.

as for the english and spanish layouts, i think the workaround by modifying the xorg.conf file should do it:

[https://bugs.launchpad.net/ubuntu/+bug/225055/comments/8](https://bugs.launchpad.net/ubuntu/+bug/225055/comments/8)

instead of gr, just put es.

a much better solution for esperanto in hardy is to use SCIM, since the esperanto keyboard will prevent you from using q,w,x, and y:

[http://ubuntuforums.org/showthread.php?p=5751130](http://ubuntuforums.org/showthread.php?p=5751130)

good luck! mucha suerte! bon&#349;ancon!

---


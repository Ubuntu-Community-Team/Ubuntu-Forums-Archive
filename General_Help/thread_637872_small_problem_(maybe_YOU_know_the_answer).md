---
title: "small problem (maybe YOU know the answer?)"
date: 2007-12-11
forum: General Help
---

### Post by Dr.Suse on 2007-12-11
i get this error everytime i login: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=52920&d=1197397021[/IMG]

does anyone know how to change a setting to keep that from coming up?

---

### Post by zeller on 2007-12-11
It's on the tip of my brain but I'm still noob. Something to do with resetting the xserver settings? I should know because I've had to go through it before. I'm feeling horrible I can't help you.

Search the forums for pc105 and pc101 keyboard settings.

Someone knows. It will get solved.

---

### Post by DarkN00b on 2007-12-11
These define what keyboard Ubuntu thinks you are using. A modern keyboard should be 104 keys or more. If your keyboard has a "windows" key then you are using at least a 104 key keyboard. You should edit your xorg.conf file and find the keyboard section and change "XkbModel" to "pc105".

Here's mine as an example:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

Alternatively, you could try going to System > Preferences > Keyboard and clicking on the Layouts tab. You can either choose your keyboard (if it is listed) or you can choose "Generic 105-key (Intl) PC".

Hope that helps.

---

### Post by strabes on 2007-12-11
If you just hit "use X settings" it won't come up anymore.

---

### Post by Dr.Suse on 2007-12-11
thanks! this has really cleared some things up for me.

---


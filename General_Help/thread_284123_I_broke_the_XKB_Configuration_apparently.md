---
title: "I broke the XKB Configuration apparently"
date: 2006-10-25
forum: General Help
---

### Post by Sirron on 2006-10-25
While I was following this tutorial; [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25) I broke it.

I think it was the "sudo dpkg-reconfigure xserver-xorg" part, when the configuration wizard was shown, I figured I should just go all the way through it, but I can't have done it right because the pounds sign on my keyboard no longer works and I get the error message:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

at logon.

It's pretty obvious that I messed up the keyboard configuration, but I'm using an Acer Travelmate laptop, and so it's got a special keyboard layout to some extent. So I don't know how to fix it.

I'm planning on upgrading to Edgy, would that fix it for me do you reckon?

---

### Post by gnomeza on 2006-11-12
> **Sirron said:**
> If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

Open a terminal, type the commands mentioned and post the output here.

---

### Post by eklem on 2006-11-19
I got the same problem. My setup is:
Edgy amd64 (upgraded from Dapper), Norwegian keyboard (105 keys), and englihs as language. I first understood that something wasn't working when I couldn't type the 'at'-sign (which is: right-ALT-key + 2)

```
xprop -root |grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "no", "no", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "no", "no", ""

```


```
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [no  no,no   nodeadkeys]
 model = pc105
 options = [grp grp:alts_toggle]
 overrideSettings = true

```

---

### Post by findus on 2006-11-20
I have the same problem - happened on a clean install of edgy, and it must have been after I reconfigured xserver-xorg to get a higher screen resolution.

---

### Post by eklem on 2006-12-11
Almost thinking of switching because of this, seems like nobody has understood that this is a real pain for lots of users.

So, the only thing we're left with is the "superstitious learning"-alternatives.

What I did:
Changed my xorg.conf to this:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "no"
EndSection

```

... and changed my keyboard preferences (System > Administration > Keyboard Preferences > Layouts > Keyboard Layout) to "Generic 104-key PC".

Which of those two made my "@"-signs appear again, and Caps Lock work I don't know.

Maybe it was the salt I was throwing over my left shoulder, or the Ubuntu-CD I sacrifized to some old norse god...

---

### Post by Malac on 2007-02-02
This is because the Keyboard Preferences is sort of broke apparently.
Open gconf-editor [Applications->System Tools->Configuration Editor]
Go to /desktop/gnome/peripherals/keyboard/kbd and remove the values in layouts and options. You will need to do this every time you alter any keyboard layout options.

---

### Post by ukripper on 2008-02-19
> **Malac said:**
> This is because the Keyboard Preferences is sort of broke apparently.
Open gconf-editor [Applications->System Tools->Configuration Editor]
Go to /desktop/gnome/peripherals/keyboard/kbd and remove the values in layouts and options. You will need to do this every time you alter any keyboard layout options.

This resolves the problem with error message Xkb after GDM starts. I have tested it before.

Cheers mate

---


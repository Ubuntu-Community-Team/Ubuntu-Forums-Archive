---
title: "Misconfigured keyboard at logon screen"
date: 2008-02-16
forum: General Help
---

### Post by flaviofaria on 2008-02-16
Hi guys,
After installing my video card driver, the keyboard got misconfigured when I type in my username and password to start using Kubuntu. After the logon screen, the keyboard works well. I don't know how to solve it, but it seems xorg.conf is ok.
Thanks for any help.

Flávio Faria

---

### Post by flaviofaria on 2008-02-24
Up

---

### Post by der_joachim on 2008-02-25
You should elaborate: what did you exactly do to configure your video card, what do you mean by 'misconfigured' and what is the intended layout or behaviour?

Depending on how your new video card was configured, your xorg.conf was probably somehow backed up. Find the backup (it should be in /etc/X11) , replace the keyboard section in your current xorg.conf with the one in your backup and restart X. Make sure that you have backed up your xorg.conf as well, to avoid more trouble (trust me, I've had my share ;)) . Your keyboard section should look like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle,compose:ralt,eurosign:5,altwin:super_win"
EndSection

```

Good luck.

---


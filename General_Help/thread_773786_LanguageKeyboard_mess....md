---
title: "Language/Keyboard mess..."
date: 2008-04-29
forum: General Help
---

### Post by neocortex on 2008-04-29
Hello!
I recently moved to Hardy and I am, generally, very happy with it. In particular, I set-up my Language and Keyboard as English/UK, and all indicators (for keyboard etc.) are showing that it is active. However, for some mysterious reasons when I type it is English/USA. Then, I set everything, again, to be English/UK, and, again, everything is fine until reboot when it goes back to USA.
Interestingly, although during installation I have chosen UK as default, now in my Keyboard Preferences USA is activated when Reset to Defaults.
What is going on? Please, how can I fix that?

Thanks in advance,
PM

---

### Post by agerio on 2008-04-29
Same problem here. I choosed Spanish-Latin America During installation (all the keys worked alright in the test field), and until this morning everything worked well with the default install, but know the keys started to change, and when I checked the Keyboard setup in the Preference Menu, it is configured in Spanish (No Latin America). I still can work but will have to find a solution soon.

---

### Post by neocortex on 2008-05-01
Hello!
Well, I believe I made some progress with this issue. If you experience similar problems, check /etc/X11/xorg.conf file and if necessary add a line in section where keyboard is specified. Here are steps:
```

> gksudo gedit /etc/X11/xorg.conf

```
Then add:
```

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    **[COLOR="Red"]Option         "XkbLayout" "gb"[/COLOR]**
EndSection

```
I added < Option "XkbLayout" "gb" >, as marked, since I have read that it is better than "uk". However, you should put specification for your prefered language.

Best,
PM

---


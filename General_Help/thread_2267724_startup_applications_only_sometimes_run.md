---
title: "startup applications only sometimes run?"
date: 2015-03-03
forum: General Help
---

### Post by Allen McBride on 2015-03-03
I wanted to remap my Caps Lock key to Control, so I put the command "setxkbmap -layout us -option ctrl:nocaps" in Startup Applications Preferences. Sometimes (that is, some logins/boot-ups) this works, some it doesn't. I don't see a pattern to it. What might cause Startup Applications to run sometimes and not others? (I tried putting the setxkbmap line in .profile, which didn't work, because apparently Unity somehow doesn't invoke a login shell?)

I'm running 14.10 on a Dell Inspiron 7737.

---

### Post by ajgreeny on 2015-03-03
I don't know anything about setxkbmap but I wonder if you need to set a sleep time to delay the command in order to ensure the DE is fully up and running before the command is run.

In the command box for startup applications try ```
bash -c "sleep 10; setxkbmap -layout us -option ctrl:nocaps
```and see if that helps out.

---

### Post by Allen McBride on 2015-03-03
Thanks! I'll give it a try and see how it goes.

---

### Post by ajgreeny on 2015-03-04
A quick edit to my suggested command, where I forgot the final quote mark.

Make it  ```
bash -c "sleep 10; setxkbmap -layout us -option ctrl:nocaps"
```

---

### Post by Allen McBride on 2015-03-04
Got it. Seems to be working so far. Thanks again!

---

### Post by ajgreeny on 2015-03-04
Great!

Once you are sure, please use Thread Tools at the top to mark this as SOLVED.

---

### Post by CantankRus on 2015-03-04
gnome-tweak-tool allows you to set capslock to ctrl as you could in keyboard settings prior to Unity.
gnome-tweak-tool has a dependency on gnome-shell-common that you may not want to install.

You can change the key in dconf without installing gnome-tweak-tool.
ie in Terminal...
```
gsettings set org.gnome.desktop.input-sources xkb-options "['caps:ctrl_modifier']"
```

---

### Post by mc4man on 2015-03-04
Just for info sake on "startup applications"
They are run thru .desktops saved in ~/.config/autostart/
So a line can be added to any of those .desktops that delays, X being seconds desired
```
X-GNOME-Autostart-Delay=[COLOR="#0000CD"]X[/COLOR]
```

---

### Post by Allen McBride on 2015-03-07
Thanks all! I marked the thread as solved (I didn't know about that feature before), and I will look into gsettings and .desktops as well.

---


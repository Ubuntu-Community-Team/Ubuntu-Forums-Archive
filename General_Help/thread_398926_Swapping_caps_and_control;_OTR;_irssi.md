---
title: "Swapping caps and control; OTR; irssi"
date: 2007-04-01
forum: General Help
---

### Post by godtvisken on 2007-04-01
Three problems I'm having Xubuntu that I didn't have with normal Ubuntu:

- with Ubuntu, I could go to Preferences -> Keyboard and swap Control and Caps Lock. I have tried doing this in my .Xmodmap, but it won't work. 

```
keycode  37 = Caps_Lock
keycode  66 = Control_L
```

- in irssi in the terminal (Terminal 0.2.5.4beta2), alt+1 no longer switches to the main server view. 

- I know that automatix is discouraged, but previously it gave me the option to install OTR, and now on Xubuntu it does not. Maybe this is a recent change with automatix. Anyway, how should I go about installing OTR for gaim? 

Thanks!

---

### Post by compiledkernel on 2007-04-01
sudo apt-get install gaim-otr 

or search for gaim-otr in synaptic.

---


---
title: "The system is running in low-graphics mode"
date: 2013-02-16
forum: General Help
---

### Post by Aleks6010 on 2013-02-16
I have windows 8 and Ubuntu 12.10 installed.
One day, I couldn't login. I wrote the correct password, it showed a black screen for a little and showed me the login screen again.
I tried [COLOR="Silver"]sudo apt-get install gdm[/COLOR] in [COLOR="Silver"]CTRL + ALT + F1[/COLOR], then I rebooted my computer. When I rebooted, it showed me a message
[IMG]http://i.stack.imgur.com/AiwJH.png[/IMG] (without the cursor)
I have a wireless mouse, so I can't use it there. When I pressed ENTER on my keyboard, it showed me another message
[IMG]http://www.deconf.com/images/itbits/software/the-system-is-running-in-low-graphics-mode.png[/IMG]
I got stuck there and ENTER doesn't do anything.
Can anyone help me?

---

### Post by Bufeu on 2013-02-16
Uninstall your graphic card drivers from a console (tty1, tty2, tty3, tty4, etc), then reboot (*sudo reboot*).

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> Uninstall your graphic card drivers from a console (tty1, tty2, tty3, tty4, etc), then reboot (*sudo reboot*).
Can you please tell me how do i uninstall it?

---

### Post by Bufeu on 2013-02-16
> **Aleks6010 said:**
> Can you please tell me how do i uninstall it?
Yes. Do you have an AMD/ATI-based or a nVidia-based graphic card?

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> Yes. Do you have an AMD/ATI-based or a nVidia-based graphic card?

I have nvidia graphics card

---

### Post by Bufeu on 2013-02-16
> **Aleks6010 said:**
> I have nvidia graphics card
```
sudo apt-get purge nvidia-* && sudo reboot
```Run this and your computer will uninstall the drivers and reboot.

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> ```
sudo apt-get --purge remove nvidia-* && sudo reboot
```Run this and your computer will uninstall the drivers and reboot.

Will it change anything in my windows 8/system or only change stuff in my ubuntu OS?

---

### Post by Bufeu on 2013-02-16
> **Aleks6010 said:**
> Will it change anything in my windows 8/system or only change stuff in my ubuntu OS?
No. It will not affect Windows 8 in any way. Please take a look at the re-edited command in my post.

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> No. It will not affect Windows 8 in any way. Please take a look at the re-edited command in my post.

Okay, I'll try it

---

### Post by Bufeu on 2013-02-16
> **Aleks6010 said:**
> Okay, I'll try it
To install it again, run```
sudo apt-get update
sudo apt-get install linux-headers* -y
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings -y
```

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> To install it again, run```
sudo apt-get update
sudo apt-get install linux-headers* -y
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings -y
```

I did what you said, still tells me about low graphics mode
Also, now TTY(number)'s resolution is now very small

---

### Post by Bufeu on 2013-02-16
> **Aleks6010 said:**
> I did what you said, still tells me about low graphics mode
Uninstall the drivers and give them a ****. After uninstalling, run ```
sudo apt-get update && sudo apt-get install xserver-xorg-video-nouveau && sudo reboot
```

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> Uninstall the drivers and give them a ****. After uninstalling, run ```
sudo apt-get update && sudo apt-get install xserver-xorg-video-nouveau && sudo reboot
```

Same thing :(
Oh, cursor now appears as X and can press stuff

---

### Post by Bufeu on 2013-02-16
Is your problem fixed?

---

### Post by Aleks6010 on 2013-02-16
> **Bufeu said:**
> Is your problem fixed?

No :/

---

### Post by Aleks6010 on 2013-02-16
Nevermind, i'll just reinstall ubuntu

---


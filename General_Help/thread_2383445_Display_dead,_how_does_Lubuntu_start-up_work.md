---
title: "Display dead, how does Lubuntu start-up work?"
date: 2018-01-25
forum: General Help
---

### Post by zaddo on 2018-01-25
Hi, 

yesterday suddenly my laptop display didn't work anymore. I have tried to attach an external display via HDMI but since Lubuntu doesn't automatically activate an attached display I don't get any signal. Therefore I would like to find out how exactly the startup procedure in Lubuntu works in order to switch to an external display without seeing anything. 

First of all, I am using Lubuntu 16.04 LTS in a dual boot with Windows 10 on a Dell Studio 1555 Laptop. My GRUB is set in a way that it will automatically boot into Lubuntu. 

1.) If an external display is attached at the HDMI port, should it automatically display something after startup? When I shut down the PC last time I had no second screen attached, so this wouldn't be preset. 

2.) After Pressing the power button to power up, does Lubuntu automatically boot into the login/password prompt or is it necessary to click somewhere? (I have only one user which is always pre-selected.) If I remember correctly, the password field is automatically selected so that I could just enter my password and press return, but I am not sure. Is that correct? 

3.) To check whether my login was successful, is there a simple way to output a short audio signal via the terminal? So I could press CTRL+ALT+T to open a terminal window and enter the "play short audio sample" command to check if I am able to login and open a terminal. 

4.) In order to activate the HDMI display I have used xrandr so far. I have created some scripts with xrandr (for mirroring the screen, selecting only HDMI etc.) and bound them as aliases to some short commands for the terminal to use a second display easily. However when trying to use these scripts (i.e. opening a terminal and entering the aliases, assuming that I have logged in successfully) the external HDMI display doesn't display anything. This is most likely due to the fact that I have a new TV (=external HDMI display) with a different native resolution that I have never used before (unfortunately the old one is gone now). Therefore I think the old xrandr scripts don't work since they assume the old resolution (HD ready) but my new TV is Full HD. My question is: If I have successfully logged into Lubuntu (and verified this with step 3.) ), what would be a suitable terminal command to receive *any* output on my external HDMI display (preferably mirroring the display to HDMI)? 

5.) In the GRUB bootup menu there are 5 options that I can select (Ubuntu, some special Ubuntu, some Memtest, some other Memtest and Windows 10). Should Windows be the last one? Could I select it by pressing "down" several times or would the selection switch up to the first entry after pressing "down" on the last entry? 
Additional note: I would prefer not to boot into Windows 10, as I need to perform a "special shutdown" to be able to boot back into Lubuntu (i.e. hold "shift" during Windows shutdown). Otherwise Windows will "block" my hard drive and Lubuntu can't boot. So it might be easier to activate the external display in Windows (Win + P) but then it would be difficult to get back into Lubuntu without any display. 

I am grateful for any other hints as well to check whether my display, the graphic chip or something else broke down. 

Regards!

---

### Post by dragonfly41 on 2018-01-25
I have recently experienced loss of laptop internal monitor.
Can you try toggling between internal monitor and external monitor by cycling through Super+P several times.

---

### Post by zaddo on 2018-01-25
Might be a dumb question: what is the "super" key? I think I have bound "open start menu" to my Win-key, therefore I am not sure what super might be.

---

### Post by dragonfly41 on 2018-01-25
Super is the key with Windows icon.
You referred to Win+P in your post.
It is that combination.

Quoting from another thread ...

"Super+P cycles between: Laptop monitor only, mirror across all three external monitors (laptop monitor off), and all 3 monitors extended (laptop monitor off)."

---

### Post by zaddo on 2018-01-25
I don't think this will work with Lubuntu (it might with Ubuntu). However as I told you I have bound a different function to the Win Key this might probably not work at all.

---

### Post by dragonfly41 on 2018-01-25
> [COLOR=#000000]However as I told you I have bound a different function to the Win Key[/COLOR]

There are many other keys you can choose for binding to avoid conflicts.

Ubuntu:

[https://help.ubuntu.com/stable/ubuntu-help/shell-keyboard-shortcuts.html](https://help.ubuntu.com/stable/ubuntu-help/shell-keyboard-shortcuts.html)

Windows:

[https://support.microsoft.com/en-gb/help/12445/windows-keyboard-shortcuts](https://support.microsoft.com/en-gb/help/12445/windows-keyboard-shortcuts)

---

### Post by zaddo on 2018-01-25
Ok this is for Ubuntu and I am using Lubuntu. I don't know how this is supposed to help me. Anyway, I will try Super+P later when I'm home. 

Back to topic, and information on my questions 1.) to 5.)?

---


---
title: "How can I remap keys for the whole system?"
date: 2022-04-04
forum: General Help
---

### Post by guilherme9 on 2022-04-04
The single ctrl key my laptop (ideapad s145-15iwl) stopped working together with the /?° key. I already checked the flat, cleaned it, did everything but they would intermittently stop and come back, until they died for good.

What I wanted to know is if there's any way to remap it to the Fn key (and the Fn key to the Windows key, which isn't used) in a way it would work for the entire system, including the terminal and hotkeys. 

So far I've only seen solutions that remap them for X and the GUI.

It wouldn't work for hotkeys, nor would it work inside a terminal. 

I needed something that worked even in runlevel 1.

Is there something for it?

Thanks!

My Ubuntu version is 18.04 LTS.

---

### Post by #&amp;thj^% on 2022-04-04
Wow all that for a cheap replacement and it's backliight: [https://www.amazon.com/Replacement-S145-15IWL-S145-15AST-S145-15API-Backlight/dp/B0895GDJ1H](https://www.amazon.com/Replacement-S145-15IWL-S145-15AST-S145-15API-Backlight/dp/B0895GDJ1H)
that  was US currency, they are not hard to replace, youtube would have a step by step.

---

### Post by guilherme9 on 2022-04-04
> **1fallen said:**
> Wow all that for a cheap replacement and it's backliight: [https://www.amazon.com/Replacement-S145-15IWL-S145-15AST-S145-15API-Backlight/dp/B0895GDJ1H](https://www.amazon.com/Replacement-S145-15IWL-S145-15AST-S145-15API-Backlight/dp/B0895GDJ1H)
that  was US currency, they are not hard to replace, youtube would have a step by step.

First of all it isn't US currency, but price isn't the issue, it's time.

After cleaning and checking the flat cable failed, I ordered a new one. But there was an issue in the delivery, it should arrive in 3 days and it looks like it will take more. 

While I wait for this to arrive (or for them to to refund me) I'm having to carry a whole keyboard with me everyday, I really can't work without a ctrl key.

---

### Post by #&amp;thj^% on 2022-04-04
Anyway, see if this can help, your first goal was a bit lofty: [https://opensource.com/article/18/11/how-swap-ctrl-and-caps-lock-your-keyboard](https://opensource.com/article/18/11/how-swap-ctrl-and-caps-lock-your-keyboard)

---

### Post by vanadium on 2022-04-05
As a quick stopgap, you could have your CapsLock key act as Control using the "caps:ctrl_modifier" xkb option. If you need Capslock, there are other options such as swapping the left Win with left Control. See Gnome Tweaks, keyboard tab, Additional layout options, or set an option with e.g. "setxkbmap -option caps:ctrl_modifier". The list of options can be found in "/usr/share/X11/xkb/rules/base.lst"

---

### Post by dragonfly41 on 2022-04-05
Can you use the virtual keyboard Florence in the mean time to get you through?

---

### Post by TheFu on 2022-04-05
Almost all keys can be remapped, but a few are directly connected to hardware stuff. If you use X/Windows, it isn't hard. There are 
The Fn is one of those connected to HW and I've never seen it remapped. 
[https://www.dedoimedo.com/computers/linux-keyboard-custom-remap.html](https://www.dedoimedo.com/computers/linux-keyboard-custom-remap.html) explains.
This is after login and X/Session startup.  Before that time or through a remote ssh connection, it won't apply.

---


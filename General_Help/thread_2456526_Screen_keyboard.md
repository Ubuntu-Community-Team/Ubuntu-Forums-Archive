---
title: "Screen keyboard"
date: 2021-01-13
forum: General Help
---

### Post by awal16 on 2021-01-13
Hi everyone,

I'm a new Linux user. I installed Ubuntu 20.04 for the first time, so I'm still learning.
Is it possible to install a screen keyboard, which is always visible (something like Windows has)? I found the one in Settings, but that one is only visible when I click in a text area, and sometimes this screen keyboard repeats a letter many, many times.

Greetz,
Anneke

---

### Post by gdesilva on 2021-01-13
Try 'onboard' which can be autostarted at boot time. If onboard is not installed you should be able to install it using the repos.

Also, check out the following for Ubuntu,

[https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-osk.html.en)

---

### Post by awal16 on 2021-01-15
Yes, I found that keyboard, but it doesn't fit my needs. It hasn't a ctr, alt, esc keys. And the keyboard doesn't popup in Synaptic. I need something like Windows screen keyboard. Small, always visible and I can place it wherever I want.

---

### Post by dragonfly41 on 2021-01-15
There is florence found in Synaptic Package Manager.

---

### Post by Holger_Gehrke on 2021-01-15
> **awal16 said:**
> Yes, I found that keyboard, but it doesn't fit my needs. It hasn't a ctr, alt, esc keys. And the keyboard doesn't popup in Synaptic. I need something like Windows screen keyboard. Small, always visible and I can place it wherever I want.

Then you obviously haven't tried to the various customization settings for onboard. After starting onboard you should have an icon in the system tray. A right click on that icon gives a menu with an option 'Settings'. Clicking on that allows you to change many aspects of onboard's look and behaviour (you can also start that settings program with 'onboard-settings from the command line). I currently have it set up as a free floating, undecorated, always on top window of about 800px by 250px showing a full keyboard (including strg, alt, Windows-key, AltGr, Menu and cursor-control keys; the numeric pad is hidden, activating it hides the normal keyboard and shows the numeric pad and a pad with user definable macro keys). 

Holger

---


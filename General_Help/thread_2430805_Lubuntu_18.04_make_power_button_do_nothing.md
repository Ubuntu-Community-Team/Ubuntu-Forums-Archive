---
title: "Lubuntu 18.04 make power button do nothing"
date: 2019-11-07
forum: General Help
---

### Post by kazhangrmi on 2019-11-07
Hi, I've been grinding my face on this problem for a couple days now and I have genuinely no idea what to try next.
I am currently attempting to make the power button on my tablet running Lubuntu 18.04 do nothing. Absolutely nothing.
Currently when I press the power button it brings up an options menu popup with Shutdown, Reboot, etc.
This is a fairly standard install of Lubuntu 18.04, I haven't installed or activated anything extra that I think would interfere with anything that handles power button actions.

My first instinct was to change the setting on the xfce4-power-manager for action taken when the power button is pressed to do nothing. Simple enough right?
Except changing that setting changes absolutely nothing and the menu still comes up.

I've tried to use the terminal to explicitly change the power button action for xfce4-power-manager to various numbers besides 3 (which it started on). 
None of them do anything, not even 4 which I'm pretty sure corresponds to shutdown.

I've tried to use the terminal to set the xfce4 power manager to turn over power button action settings to systemd and then set the logind.conf file in systemd to ignore the power button being pressed.
Still the menu comes up. Though if I set logind.conf to shutdown when power button is pressed the tablet shuts down when pressed.


Does anyone have any idea how I can either fix xfce4-power-manager so it actually properly sets the power button press action to "Do Nothing" or have any other workarounds to achieve this?

---


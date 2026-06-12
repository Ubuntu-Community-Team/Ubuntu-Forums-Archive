---
title: "Ubuntu 22.04 TLS does not Suspend from Login Screeen"
date: 2022-05-14
forum: General Help
---

### Post by dabezt on 2022-05-14
I've a workstation at home (intel i5, etc.) with Ubuntu desktop installed with Gnome. I had Ubuntu Desktop 21.10 installed and I did an Upgrade to 22.04... 

Before upgrading the computer goes to Suspend (sleep) from the login screen...
But now 22.04 does not go to Suspend...

I've configured the system loged into gnome graphic environment, went to Settings, Power, I've balanced, but I configure to go to sleep / suspend after 15 minutes. I logged off, and let the system into login screen.
And it does not go to Suspend after 15 minutes... why?

I've also tried to configure gnome: "gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 900" and it continues without suspending / going to sleep

If I access to ubuntu through ssh I run "[FONT=var(--ff-mono)]systemctl suspend" and indeed it goes to suspend mode ¿?

Thnx![/FONT]

---


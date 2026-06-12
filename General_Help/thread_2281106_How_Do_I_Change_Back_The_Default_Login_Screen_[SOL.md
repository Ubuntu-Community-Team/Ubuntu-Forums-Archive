---
title: "How Do I Change Back The Default Login Screen? [SOLVED]"
date: 2015-06-04
forum: General Help
---

### Post by LoDw5Im on 2015-06-04
I've installed another UI, and now my login screen has a white box that says my username and password.
If I click on my username, it changes to something else and also to Ubuntu 12.04.5.

I've tried reinstalling Ubuntu-desktop, making sure the configuration says Ubuntu-greeter, and session-ubuntu unity.
Is there a way I can restore it without having to reinstall Ubuntu?

I've got it:
sudo apt-get autoremove lightdm
sudo apt-get install --reinstall lightdm-gtk-greeter

Worked for me. The different thing is that that was a big bubble at the top about my internet connection, never seen that before. I've choose to not show it again.
I will now add that to my Ubuntu lists and references document.

---

### Post by TheFu on 2015-06-04
There is a danger using the same config files for different desktops. There are 2 ways to solve this.
a) create a different userid and login with that one for any DE you are testing.
b) mv ~/.config/ to a backup location, then logout and login with the new DE you are testing. This way, all the different settings don't get mixed up between the different GUIs.

Lastly, it is best to have only 1 DM - Display Manager (really a login manager) - install on a system. Switching between different DEs, WMs doesn't require changing the DM.

Clear as mud?

---


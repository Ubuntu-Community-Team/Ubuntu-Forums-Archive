---
title: "Cannot disable automatic update check (Software Updater)"
date: 2019-04-03
forum: General Help
---

### Post by ahotep on 2019-04-03
Hey all! First post, so if I missed something, please go easy on me. I did scour the forum for existing threads addressing my particular issue, but came up empty. So, here's the deal:

I can't seem to effectively disable automatic update checks in Software Updater (Ubuntu 16.04). I've set it to "Never" in the settings (see screenshot), but it still pops up regularly and prompts me to install available updates. Is this a bug, or am I just doing something wrong? I want to run manual checks via SU or apt-get *only*, with zero automatic checks. How do I make that happen?

Not that it really matters (since this should work regardless), but the reason I'm trying to disable automatic update checks is that SU checking for updates routinely crashes my OpenVPN client (or rather severs the connection and prevents it from reconnecting somehow). It's not the end of the world, since I have a kill switch, but it does get annoying. I've tried to solve this specific issue first, but haven't been able to, even with extensive support from my VPN provider. SU running an automatic update check is definitely the cause (happens every time when and *only* when a prompt for available updates appears), but it's completely unclear why. It doesn't happen when I run the same check manually (either with SU or with apt-get). Makes things even more weird, but at least it works. So, the easiest fix at this point is to just disable automatic checks and check for and apply updates manually.

[ATTACH=CONFIG]282928[/ATTACH]

---

### Post by ajgreeny on 2019-04-03
Have a look in the list of programs that start when you boot the computer or start a new session and you may find that **Update-manager** or something similar is still enabled.
If so disable it and see if that helps your problem go away.

I use Xubuntu 18.04 and have disabled the update-manager and also removed the **unattended-upgrades** package; it does, of course, mean that I must do all this manually, but I prefer to do it at my time of choosing and not when the system decides to do so.

---

### Post by ahotep on 2019-04-03
Thanks for the input. The only way I know how to check this is via Startup Applications, and that doesn't list Software Updater. Is there another place it could be "hiding"?

---

### Post by ajgreeny on 2019-04-03
Have a look in /etc/xdg/autostart/ to see if the startup is configured there; that's where the various .desktop files are in Xubuntu but I'm not sure about Ubuntu.

---

### Post by ahotep on 2019-04-04
This is what I have in /etc/xdg/autostart. I see update-notifier.desktop there. But I'm not sure if that's what I'm looking for.

[ATTACH=CONFIG]282943[/ATTACH]

---

### Post by webaake on 2019-04-04
In the link there are two ways of disabling automatic updates: [https://www.garron.me/en/linux/turn-off-stop-ubuntu-automatic-update.html](https://www.garron.me/en/linux/turn-off-stop-ubuntu-automatic-update.html)

I have it disabled too but I run manual updates everyday.

---

### Post by ahotep on 2019-04-04
Thanks for the link. I just tried the CL option, but it turns out all my settings are already disabled (presumably from setting it to never in the GUI). But Software Updater still pops up regardless.

[ATTACH=CONFIG]282947[/ATTACH]

---


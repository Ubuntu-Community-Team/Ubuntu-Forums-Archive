---
title: "no desktop/command line/ malformed URL /system ??"
date: 2008-03-11
forum: General Help
---

### Post by Col. Mustard on 2008-03-11
I am getting some pretty bad problems with Kubuntu 7.10... I've had it for a couple days, and after finally getting wifi to work and installing my nvidia driver, I am getting problems when I boot... I get errors that tell me 
```
MALFORMED URL /system
and
/trash
```
and also I get a popup "Information KDESuDo" ```
No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...
```
also I cannot see any wallpaper, just a solid blue screen with no icons or files, I cannot acces the desktop, and when I go to "system menu" next to the K menu icon, there is no home, root, storage media, nothing... its just completely blank. what has gone wrong now? I've tried troubleshooting this on my own, but after nearly screwing more things up, I've decided to ask for some assistance with this one... Anyone have any ideas? hopefully its fixable... even though I've only had it installed a few days, I've spent over 45 hours just trying to get as far as I am now :-# Thanks for reading EDIT: and also, I can't access "Run Command" from the K menu, I click it and nothing happens. methinks not good <.<



**[COLOR="Red"][SIZE="4"][SOLVED][/SIZE][/COLOR]** to fix this, enter konsole and type the command line ```
sudo apt-get install kubuntu-desktop
```followed by pressing CTRL+ALT+BACKSPACE, and then typing the command line ```
startx
```

---

### Post by siofwolves on 2008-03-15
Col. Mustard, thank you so much.

This really helped me. I had installed kde4 and removed it, since then I had problems booting.

I was having "kinit : No resume image, doing normal boot..." problems.

I had read somewhere else to check the file /etc/X11/default-display-manager to make sure it had /usr/bin/kdm in, which it did.

I to re-install kdm at that point as it had gone missing...

```
sudo apt-get install kdm
```

After that I could boot, but got the malformed URL system:/ & trash:/ errors that bought me here.

```
sudo apt-get install kubuntu-desktop
```
Works great, after a reboot I'm back to where I was.

Thanks again.

---


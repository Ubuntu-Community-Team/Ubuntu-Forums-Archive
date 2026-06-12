---
title: "How to switch to reinstall default gnome shell extensions after unistalling them?"
date: 2020-12-16
forum: General Help
---

### Post by EngineerStrange on 2020-12-16
I have mistakenly removed all the gnome shell extensions in ubuntu 20.04 using the command
sudo rm -r /usr/share/gnome-shell/extensions/
Now I can't reinstall them. Please help.

---

### Post by DuckHook on 2020-12-16
There's no easy way to just bring everything back. When using sudo rm -r, as you have discovered, you are playing with live dynamite.

You could try a file recovery tool like photorec. It's only fair to warn you that this will be like pulling teeth. Detailed instructions here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

The "easier" way is to reinstall gnome shell: ```
sudo apt install --reinstall gnome-shell
``` This will get you back to a working shell. It will ***not*** bring back your lost custom extensions. You will have to reinstall those. It will probably also nuke any other customizations that you have made to your look and feel since your initial install. But that should be a small price to pay for a working system.

Why were you diddling around in critical system files? If exploring (which I do encourage) don't do so on your base install (which I highly discourage). Instead, fire up a VM and do all of your experimentation on that. You can simply roll back to a known good snapshot when things go wrong.

---

### Post by deadflowr on 2020-12-16
Reinstalling ubuntu-desktop will reinstall the default extensions.
```
sudo apt install --reinstall ubuntu-desktop
```
if you had the extra extensions package then reinstall that too
```
sudo apt install --reinstall gnome-shell-extensions
```

As you only removed the /usr/share sub directories files all extensions in that location are from the Ubuntu repository.
(Extensions installed directly from the gnome shell extensions web site are installed to your user's home local directory ((~/.local/share/gnome-shell/extensions)

You can search available repository extension packages with
```
apt search gnome-shell-extension
```
this will also hint at which have been installed
You can then apply the apt install --reinstall command to those marked as such.

(You can also use dpkg to list which are supposedly installed like
```
dpkg -l | grep gnome-shell-extension
```

Hope it helps

---

### Post by Impavidus on 2020-12-16
The command```
dpkg --search /usr/share/gnome-shell/extensions/
```will list all packages that had files installed in that directory. Reinstalling those packages should bring them back.

---

### Post by EngineerStrange on 2020-12-16
What will happen to my personal files if I reinstall Ubuntu Desktop?

---

### Post by deadflowr on 2020-12-17
> What will happen to my personal files if I reinstall Ubuntu Desktop?
Nothing.
apt only deals with system files.
Files in Home, (or in removable media locations like /media, /mnt, /srv, or other non-system folders; folders you created) will not be touched.

But if it worries you backup your files first.
Or backup your files anyway. It's a good habit to have.

---


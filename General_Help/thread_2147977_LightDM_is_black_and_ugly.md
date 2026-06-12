---
title: "LightDM is black and ugly"
date: 2013-05-23
forum: General Help
---

### Post by elliotn on 2013-05-23
guys how do i fix my LightDM login, background is black and the rest looks like its a windows 95 thing, original install was lubuntu 13.04 then i installed ubuntu through terminal.

---

### Post by ohnonot on 2013-05-24
[s]dude, how did you get your post count so high without learning anything?[/s]my apologies! that was uncalled for.
how about 'man lightdm' - there's config files which tell it which theme to use.
also, what's "installed ubuntu through terminal" supposed to mean

---

### Post by elliotn on 2013-05-24
> **ohnonot said:**
> dude, how did you get your post count so high without learning anything?
how about 'man lightdm' - there's config files which tell it which theme to use.
also, what's "installed ubuntu through terminal" supposed to mean?

lol never take stats serious...... can u tell me which commands to use

---

### Post by galgalesh on 2013-05-24
We cannot help you until you tell us what you mean by "installed Ubuntu through terminal". That's as specific as saying "I ate something blue and then my stomach hurt". Which packages did you install? Which settings did you change?

---

### Post by elliotn on 2013-05-24
the install was lubuntu then in terminal I did sudo apt-get ubuntu-desktop

---

### Post by galgalesh on 2013-05-24
First, the background of the login screen should look like the wallpaper of the user that is selected. If no user is selected, the default wallpaper is chosen.

Are you sure you switched to lightdm? You can switch to lightdm by running
*      sudo dpkg-reconfigure lightdm*
After that choose "lightdm" as window manager.

If that doens't help, maybe removing lubuntu-dekstop helps..

---

### Post by elliotn on 2013-05-24
thanks will try that

---

### Post by pqwoerituytrueiwoq on 2013-05-24
Lightdm login screens are controlled by these files, depending on if you installed ubuntu or a variant of it
[FONT=courier new]/etc/lightdm/lightdm-gtk-greeter.conf
/etc/lightdm/lightdm-gtk-greeter-ubuntu.conf[/FONT]

it can be changed by editing this file (line 2)
[FONT=courier new]/etc/lightdm/lightdm.conf[/FONT]

---


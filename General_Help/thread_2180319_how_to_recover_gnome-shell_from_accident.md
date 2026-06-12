---
title: "how to recover gnome-shell from accident"
date: 2013-10-12
forum: General Help
---

### Post by widon1104 on 2013-10-12
[COLOR=#000000][FONT=lucida Grande]      I use "rm ~ -rf" by mistake, some files in $HOME were deleted and I found out I can not go into gnome-shell again.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]      I can't find a way to recover,  I use gnome-session-fallback now.I don't want to reinstall my system.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]      My distribution is ubuntu12.04.[/FONT][/COLOR]
[COLOR=#000000][FONT=lucida Grande]      gnome-shell version is 3.4.
      What can I do now?[/FONT][/COLOR]

---

### Post by philinux on 2013-10-12
I would first try reinstalling gnome-shell from synaptic SC or terminal.

---

### Post by widon1104 on 2013-10-12
widon@widon-F3JR:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

I do not delete gnome-shell, I only remove some configuration from my $HOME.

---

### Post by philinux on 2013-10-12
> **widon1104 said:**
> widon@widon-F3JR:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-shell is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

I do not delete gnome-shell, I only remove some configuration from my $HOME.

```
sudo apt-get install --reinstall gnome-shell
```

---

### Post by widon1104 on 2013-10-12
> **philinux said:**
> ```
sudo apt-get install --reinstall gnome-shell
```
Thank you for your reply, but it does not work.

---


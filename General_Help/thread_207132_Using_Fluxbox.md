---
title: "Using Fluxbox"
date: 2006-07-01
forum: General Help
---

### Post by paparucino on 2006-07-01
Hi guys,
hope this is the correct place for this question.
I'ld like to use Fluxbox instead of Gnome-gdm. I've already installed fluxfox, but I on't know where instruct Ubuntu to run Fluxbox.

Can you help me?
Thank you in advance

---

### Post by thasheep on 2006-07-01
This is really a two-stage process. Firstly, stop gdm from starting at boot by marking the relevant initscript not executable.

sudo chmod 644 /etc/init.d/gdm

Now, add this line to /etc/rc.local, before the line "exit 0"

su -c startfluxbox - paparucino

Change paparucino to whatever username you want to log in automatically.
I have to admit I've never used fluxbox on ubuntu (have with other distros) so I've never done this exactly. However, it should work :) Let us know how you go.

To revert to standard behaviour, remove or comment (#) out that line in rc.local and make the gdm initscript executable again.

sudo chmod 755 /etc/init.d/gdm

---

### Post by paparucino on 2006-07-01
[QUOTE=thasheep]This is really a two-stage process. Firstly, stop gdm from 
[...]
sudo chmod 755 /etc/init.d/gdm[/QUOTE]
Well... I tried your solution but it doesn't work correctly. gdm must have 755 permissions or the system crashes when you logout. I've restored the original permissions and removed the command from rc.local then logout. In the options (bottom left) I select to change windows manager and magically fluxbox was there. Checked. Then I was asked if I wanted fluxbox as the default wm. Everything is now ok without modifying any file. Let the software work for us. :-) 
Thank you very very much for you suggestions, they were helpful for me.

---

### Post by scxtt on 2006-07-01
you can use gdm and fluxbox ... just log out of a gnome session and you should be able to select fluxbox from the "sessions" menu - it worked for me ... but once it started using fluxbox, the menu editor crashed on me and corrupted the config file, so i had no menus - i then gave up on fluxbox cause i like gnome anyway ...

---


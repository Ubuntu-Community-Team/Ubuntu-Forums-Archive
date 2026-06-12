---
title: "Brand new to Linux and Ubuntu"
date: 2006-10-16
forum: General Help
---

### Post by David McSpadden on 2006-10-16
I installed LAMP from a 6 iso image.
It seemed to run fine through the install.
It reboots and then asks for a login.
I use the user generated during install.
Now I am just sitting at a command prompt.
How can I get the GUI interface?

---

### Post by aktiwers on 2006-10-16
have you tried typing

> startx?

---

### Post by David McSpadden on 2006-10-16
startx returns:
-bash: startx: command not found

---

### Post by taurus on 2006-10-16
Sounds to me like you installed the server version.  Now, you need to install Gnome so at the prompt, type

```

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by David McSpadden on 2006-10-16
That sounds good but I don't have this on a public facing network.
Will it be ok if sudo aptitude update can not get to the sites it is trying to get to??

---

### Post by David McSpadden on 2006-10-16
I have opened up the router this is connected to.
Should I see Buffer I/O error on device hdc while it is downloading?

---

### Post by tminuszero on 2006-10-16
What do you mean it's not on a "public facing network"? Do you meant that it's only on a private network, but not attached to it's own keyboard/video/mouse?

You said that you installed LAMP - I assume that this is for a file or development server and not a workstation?

If aptitude isn't getting to the sites, then it means that you may have some internet connection problems. Can you get access to anything in your network from the new linux install? Can you access anything outside? Try this:

ping 192.168.1.1 (or whatever your router IP address is)

And then:

ping ubuntuforums.org

Is it connecting?

---

### Post by PriceChild on 2006-10-16
If you need a gui, you might fare better installing a standard gnome or kde from the disc, then adding the lamp packages yourself.

---

### Post by etcpool on 2006-10-16
install LAMP from server cd first , then let


sudo apt-get install xubuntu-desktop


take the rest.

it's not that rich-featured desktop

but it's fast and then you can use synaptic to add pieces of softwares to satisfy your need.


hope this help.



etc,

---


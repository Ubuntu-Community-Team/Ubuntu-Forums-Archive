---
title: "start programms"
date: 2007-01-04
forum: General Help
---

### Post by jmvidalvia on 2007-01-04
¿is there anyway to edit start programs from console instead of using Gnome-session-properties?
I would like to add new programs with a script like: echo program_name >> ???????.
Thank you!

---

### Post by bruenig on 2007-01-04
The startup programs are stored in ~/.config/autostart
You ought to be able to open up one of those, see how it is formatted and go from there.

---

### Post by jmvidalvia on 2007-01-04
Mistery!: my ~/.config/autostart is empty (ls -la shows nothing) although I have programs in session start.
I use Gnome in Edgy

¿¿??

---

### Post by jmvidalvia on 2007-01-04
I found it:

./etc/xdg/autostart
./usr/share/gnome/autostart
./home/jm/.config/autostart

Seems that those 3 directories can have autostart programms.
:-)

---

### Post by bruenig on 2007-01-04
> **jmvidalvia said:**
> I found it:

./etc/xdg/autostart
./usr/share/gnome/autostart
./home/jm/.config/autostart

Seems that those 3 directories can have autostart programms.
:-)

/home/jm/.config/autostart is the same as ~/.config/autostart like I said and is the one where user added autostarts tend to go (since you have permissions to write there).

---

### Post by jmvidalvia on 2007-01-05
Thank you!
I knew that about ~.
The mistery whas it was empty.
Now I know my autostart files are in ./usr/share/gnome/autostart.
What I don't understant is why my system is putting them in ./usr/share/gnome/autostart instead of ~/.config/autostart.
Thanks.

---


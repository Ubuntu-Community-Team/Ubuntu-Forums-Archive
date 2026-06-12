---
title: "Running remote GTK applications"
date: 2007-04-03
forum: General Help
---

### Post by KanadaKid on 2007-04-03
Hi,

I'm using Ubuntu Edgy, and I seem to have run into a problem trying to open GTK applications remotely. By this, I mean that I ssh'd into another Linux box (Redhat 9) through the command line, and tried to open gedit likewise. However, I get this error:

> (gedit:13719): Gtk-WARNING **: cannot open display:  

I'm not sure what I did wrong, considering that this worked just fine on my previous installation of Mandriva before I changed over to Ubuntu. I'm sure it's something basic that I might have forgotten, but at this point, I basically can't figure out what to do. Perhaps I'm missing some packages that I'm not aware of?

Any ideas? Thanks in advance!

---

### Post by Jussi Kukkonen on 2007-04-03
Do you have x-forwarding enabled (both in your ssh config and in the remote ends sshd config)?

---

### Post by KanadaKid on 2007-04-04
Indeed, X11 Forwarding was disabled in my ssh config file. Enabling it worked like a charm. :)

Thanks!

---


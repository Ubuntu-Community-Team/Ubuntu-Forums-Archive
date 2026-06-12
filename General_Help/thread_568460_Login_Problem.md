---
title: "Login Problem"
date: 2007-10-05
forum: General Help
---

### Post by anko-dw on 2007-10-05
Every time I login to my Ubuntu, always there a massage like this:

user`s $ HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User`s $ HOME directory must be owned by user and not writeable by other users.



What does it means and what should I do to make that massage disappear?

---

### Post by kire3 on 2007-10-05
Hello,

I also have a problem when i login in the system. It says that the GNOME can't log me in because the hard  disk is already full. Is there any way to delete some of my unused files?

Need your advice.

Thanks  

Kire
Phil

---

### Post by strabes on 2007-10-05
> **anko-dw said:**
> Every time I login to my Ubuntu, always there a massage like this:

user`s $ HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User`s $ HOME directory must be owned by user and not writeable by other users.



What does it means and what should I do to make that massage disappear?

It means that there's a problem with the premissions of your ~/.dmrc file. Run the following command in a terminal (Applications, Accessories, Terminal)```
sudo chmod 644 ~/.dmrc && sudo chown YOURUSERNAME:YOURUSERNAME ~/.dmrc
```




> 
I also have a problem when i login in the system. It says that the GNOME can't log me in because the hard disk is already full. Is there any way to delete some of my unused files?

Need your advice.

A quick [google](http://www.google.com/search?q=gnome+login+disk+full) of "gnome login disk full" revealed several pages with good advice:

[https://bugs.launchpad.net/gdm/+bug/35217](https://bugs.launchpad.net/gdm/+bug/35217)
[http://bugzilla.gnome.org/show_bug.cgi?id=144473](http://bugzilla.gnome.org/show_bug.cgi?id=144473)

---


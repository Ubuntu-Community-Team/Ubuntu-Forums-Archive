---
title: "If i sudo into pcmanfm and trash something... how do i empty trash??"
date: 2016-06-22
forum: General Help
---

### Post by a.dusty.trail on 2016-06-22
If i sudo into pcmanfm and trash something... how do i empty trash??

i just get permission denied on the file that i trashcanned as sudo..

i cant go to trashcan as sudo.. 
trash:///
is not  someplace sudo pcmanfm can go....

---

### Post by TheFu on 2016-06-22
Using sudo with any GUI tool is a bad idea. You've just seen 1 of the repercussions. There are many others, which are undesirable.

If you must use a GUI tool with elevated permissions, try [s]**sudo -h program**[/s]. CORRECTION: **sudo -H program**

Another common thing I see on the internet is people saying to **sudo gedit**. Don't do that if gedit isn't your primary editor and you haven't already set all the options you want.  Use **sudoedit** instead.  It is just easier to always use sudoedit, which is always safe - works on desktops, local and remote servers.

---

### Post by a.dusty.trail on 2016-06-23
> **TheFu said:**
> Using sudo with any GUI tool is a bad idea. You've just seen 1 of the repercussions. There are many others, which are undesirable.

If you must use a GUI tool with elevated permissions, try **sudo -h program**.

Another common thing I see on the internet is people saying to **sudo gedit**. Don't do that if gedit isn't your primary editor and you haven't already set all the options you want.  Use **sudoedit** instead.  It is just easier to always use sudoedit, which is always safe - works on desktops, local and remote servers.

:~$ sudo -h pcmanfm
sudo: unable to resolve host pcmanfm


people usually take the easiest way to do something...
and the easiest way to delete a administrateor owned file 
is to sudo into your favorite gui file manager and delete it..

---

### Post by TheFu on 2016-06-23
Sorry - I don't use it very often. Try **sudo -H program**. BTW, the manpage has lots of info about using sudo. No need to wait for someone to explain.

The easiest way to delete an admin-owned file is **sudo rm /path/to/file** - IMHO.

---

### Post by QDR06VV9 on 2016-06-23
> **a.dusty.trail said:**
> :
people usually take the easiest way to do something...
and the easiest way to delete a administrateor owned file 
is to sudo into your favorite gui file manager and delete it..

Of course, any graphical commands should use a graphical frontend like gksu/gksudo, and not sudo directly.

> Graphical sudo

You should never use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo).

Recent versions of some flavours might not have gksu installed.

If necessary install and set gksu-properties to sudo.

Examples:

gksudo gedit /etc/fstab

or

kdesudo kate /etc/X11/xorg.conf

    To run the graphical configuration utilities, simply launch the application via the Administration menu.

    gksudo and kdesudo simply link to the commands gksu and kdesu
Source:[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)
Just some Friendly Advice...

---


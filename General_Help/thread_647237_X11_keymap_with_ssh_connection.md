---
title: "X11 keymap with ssh connection"
date: 2007-12-22
forum: General Help
---

### Post by cabaro on 2007-12-22
Hi

Here is the problem:

Desktop: Ubuntu Gutsy 64bit running openssh-server with X11 forwarding

Laptop: iBook G4 osx Tiger with X11 ssh connection to Desktop

For some reason with the xterm ssh from my laptop the keymap is just fine, but when i start any X application from the ssh session the keymap changes to gibberish, i get 'j' for presssing enter and so on. 

So is it gnome changing the keymap, when i start an X application (like exaile)?

How to fix this? 
If you need any config files, just let me  know.

/cab

---

### Post by cabaro on 2007-12-22
Anyone have a clue how to fix this?

My keyboard is set to fi locale.
The connection is from X11 running on top OSX Tiger with ssh -Y command.

The keymap gets all messed up when i open any X application remotely.

When i login to my desktop (Ubuntu) it complains that my X11 keymap settings are different than Gnome settings, reset or keep gnome settings (or something like that).

Even if i open a new xterm window in my apple laptop, the keymap is already messed up after launching a X application. Unless i close the X11 program and restart it (on apple).

Anyone?

---

### Post by cabaro on 2008-01-08
Doesn't anyone have any clues for what to check?

For example; i start an ssh connection with X forwarding. The keymap is just fine using the remote console. Then i start gnome-session remotely and i get a gnome session with panels and all, everything is working fine. Except for the keymap, which is then screwed to gibberish.

I can give you config files as needed.

/Cab

---

### Post by cabaro on 2008-01-16
Is there anyone willing to help and debug this with me?

It's really annoying, i can use the ssh connection normally until i start any X program. After that the keymap is all screwed giving some wierd results on the screen.. I have to restart my ssh connection to correct this.

This all started after i did a fresh install of Gutsy. Everything worked fine on Edgy.

My keymap in gnome settings is 'Fi' and also in my Xorg.conf it's fi.

Also after this happens, the nextx time i log in locally, i get this warning about mismatching keboard layouts and the option to use X settings or to keep gnome settings. Seems to be related.

I also found quite similar thread somewhere having the same problem with gutsy, ssh, gnome and vnc connection.

Any help or comment would be appreciated.

/cabaro

---

### Post by ifishfortorque on 2008-02-01
Cabaro, 

I'm having the same problem -- usually the keymaps work fine, but when I run a kvm session over ssh from my Mac (OS X 10.4) laptop to my Gutsy desktop, the keys get all mungled around.  The 'j' => enter, enter => '8', delete => 'e' thing sounds like what I've got, but I have keymap 'us' on both ends.  

Anyone have any ideas?

---

### Post by cabaro on 2008-02-08
Yep, Sounds like the same problem i've been having.

Any config files, i should send?

---

### Post by cabaro on 2008-02-15
So nobody is commenting on this one?

It's quite annoying not to be able to start any X programs through ssh, without scrambling the keyboard.
I'd be more than happy to send any config files needed to sort this one out.

---

### Post by cabaro on 2008-02-15
I'm starting to luse faith here mates. Should i go banging on other doors here? If this is not the right forum to ask this, i can go ask somewhere else, but i thought that at least someone would be interested.
I'm not sure if ubuntu or gnome is to blame for this bug, it might even be osx's implementation of X or openssh, but i thought i presented my problem so that someone could give me a clue on where to start.
As i said before, i am willing to send needed config files, give more specific info on the problem and i am willing to do some tinkering on this one.

Rgds.

---


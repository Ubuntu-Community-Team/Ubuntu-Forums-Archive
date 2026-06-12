---
title: "Broken Edgy"
date: 2006-12-02
forum: General Help
---

### Post by John Jones on 2006-12-02
Yesterday I tried to install Beryl following the method given in the Wiki.

Now I can log in, but I don't get my desktop. I can still do CTRL-ALT-Backspace, so the system hasn't locked up. I've re-instated the original xorg.conf file, but that hasn't helped.

What I'd like to do (I think), is disable Beryl in the Startup manager, but I can't figure out how to do that from the terminal. Incidentally, I also can't figure out how to get the terminal display to pause so that I can look at the whole of a DIR, for instance, instead of only the bottom half.

I've got three books (The Official Ubuntu Book, Ubuntu hacks, Linux for Dummies), and I can't find anything that helps in any of them.

Please help a confused old man.

Thanks,

John :(

---

### Post by tommcd on 2006-12-02
Well, to get the terminal to show the entire output that you can scroll through pipe the command through less or more like this:
command | less, or command | more.
Sorry, I have no experience with Beryl.

---

### Post by John Jones on 2006-12-02
Thanks for coming back with that advice; I'll give it a go.

I'm not sure that experience with Beryl is required; what I need to do is disable an application before it starts. There is info on doing just that in the books I mentioned, but I can't figure out how to find the right thing to disable.

If it wasn't for the fact that I've been running this incarnation of Edgy for several months now, and have thereby accumulated lots of stuff I'd rather not lose, I'd just shrug my shoulders and start again. That'll teach me to to try to fix something that isn't broke. (Well, it is now, obviously!).

Thanks again,

John

---

### Post by Ramses de Norre on 2006-12-02
You can launch X with only a terminal in gdm (I think the option is called fail safe terminal or something) and then you can run gnome-session-properties to get to the start up programs dialog.

---

### Post by John Jones on 2006-12-02
Okay, I tried that and got the following messages (had to write them down & type them in here, so they may not be 100%); -

gnome-session-properties:4645

Critical**: gnome session manager-protocol_new: assertion 'GNOME_CLIENT_CONNECTED (gnome_client)' FAILED

gnome-session-properties:4645

WARNING**: Could not connect to gnome-session.

Means nothing to me, can you help, please?

John

---

### Post by John Jones on 2006-12-03
My Edgy is no longer broken;

I couldn't get into Gnome-Session-Properties, so eventually I installed Ubuntu on hdb, mounted hda (with difficulty), and deleted everything that had 'Beryl' in the name. After I did this, I was able to boot ok, and clean up.

Thanks to Tommcd and Ramses de Norre  for their assistance.

John :D

---


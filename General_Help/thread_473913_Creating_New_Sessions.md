---
title: "Creating New Sessions"
date: 2007-06-14
forum: General Help
---

### Post by Sweet Mercury on 2007-06-14
(This is from another thread, I figured it might be better suited for it's own thread.)

> **eentonig said:**
> I have it running like that. I have a seperate session that's starts Beryl and another with plain old Gnome. 

I used a Howto from the Beryl website to create the Beryl GDM session entry.

Yeah, I'm seeing a few HowTos like that myself.

This is definitely something that shouldn't be as difficult as it seems, considering there is a sessions manager built in to the UI.

edit: The "Yelp" desktop help, when I push the *Help* button in the Session manager, says that under the "Sessions" tab (which isn't there), should have an "Add" session button which should allow users to Add a new session.

I tried launching the session manager as root to see if that option would be available, but I couldn't do that.

I'd like to keep my current sessions as-is, and create duplicates to start experimenting with advanced customization. Seems like it should be a simple operation.

Can I copy and rename the session files in */usr/share/xsession * (for instance, Copy GNOME to a session called GNOME-Exp) and use the second to play with without damaging my system? Will the new file show up as an option in my login?

Thanks.

---

### Post by borris.morris on 2007-06-14
It should.

---

### Post by ncappel1 on 2007-06-16
I tried the above method on my system76 laptop but was confused as each time I tried to copy the file nothing would happen. the system kept telling me that the file didn't exist. I noticed that in the terminal the name of the file was not GNOME, as was being shown in the GUI, but gnome.desktop. I copied it to the same directory and renamed it to gnome2.desktop, and it seemed to work, but each file in the gui was named GNOME, and in the sessions chooser at login I now have two entries that read GNOME. 

What's happening? How can I give the new one a different name, like Gnome2? What's more is that I still can't edit either of the two files, not even as root. anybody know what's going on?
:-k

I also thought to add a link to another thread that is discussing this same topic, as a reference.
[http://ubuntuforums.org/showthread.php?t=445569](http://ubuntuforums.org/showthread.php?t=445569)

---

### Post by Sweet Mercury on 2007-06-17
> **ncappel1 said:**
> I tried the above method on my system76 laptop but was confused as each time I tried to copy the file nothing would happen. the system kept telling me that the file didn't exist. I noticed that in the terminal the name of the file was not GNOME, as was being shown in the GUI, but gnome.desktop. I copied it to the same directory and renamed it to gnome2.desktop, and it seemed to work, but each file in the gui was named GNOME, and in the sessions chooser at login I now have two entries that read GNOME. 

What's happening? How can I give the new one a different name, like Gnome2? What's more is that I still can't edit either of the two files, not even as root. anybody know what's going on?
:-k

I also thought to add a link to another thread that is discussing this same topic, as a reference.
[http://ubuntuforums.org/showthread.php?t=445569](http://ubuntuforums.org/showthread.php?t=445569)

I was actually able to find the */use/share/xsession* folder through nautilus, copy the file, and rename as I chose. I wasn't on as root either...

---

### Post by borris.morris on 2007-06-18
No need to be root to read/copy.

---


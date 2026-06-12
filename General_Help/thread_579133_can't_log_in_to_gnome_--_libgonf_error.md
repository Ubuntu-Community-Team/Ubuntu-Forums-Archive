---
title: "can't log in to gnome -- libgonf error"
date: 2007-10-18
forum: General Help
---

### Post by ridetheteapot on 2007-10-18
Hi today i had a horrible time getting to log into gnome.

an error message was popping up telling me that "Te file that contains your preferences is currently in use" and then some stuff about maybe someone else was logged on, which was not the case.
the error message gave me the ption to log out or continue, when i pressed continue i got a new error message -- this one is long and i'm gonna type it verbatim--

Could not resolve the address "xml:readonly:/etc/gcong/gconf.xml.mandatory" in the configuration file "/etc/gconf/2/path" Failed: Couldn't locate backend module for 'xml:readonly:/etc/gconf/gconf.xml.mandatory'

then i was force to logout.
I logged into tty and checked out the files listed in the error and they existed, with (i'm pretty certain) correct permissions. Then i checked out ~/.xsession-errors which told me i was missing /usr/lib/libgconf2-4/2/libgconfbackend-xml.so . i looked into the libgcong2-4/2/ folder and saw 2 files one of which was libgconfbackend-oldxml.so ... so i copied it as the missing file and tried to log on.... the error messages where gone but i got only a blank screen so i deleted the file and tried to log on again... 
i had some of my normal settings, with a few quirks (some new trash and home icons, different transparency and gnome-panel throwing up already running errors constantly)... i used synaptic to reinstall gconf and gnome-session (i do not know how to to this with aptitude or apt-get without removing them first), logged out and back in and now it seems to work.. and there is a file in my libgconf/2 folder called libgconfbackend-xml.so .

i havent really got a clue how i got this error to occur, but what im more worried about is that the hackish way i got gnome back will have any log term consequences.

btw i have noticed on shutdown recently i'm getting a message along these lines--
network-manager libhal shutdown failed.
does this have something to do with that problem and how might i fix it... 
recently i uninstalled network manager but have since reinstalled it.

well thanks if anyone can help, or at least i hope this thread might help someone else deal with this problem if it happens to them

---

### Post by ridetheteapot on 2007-10-21
nobody ........
anybody .......

---

### Post by trooperchix on 2007-12-06
Dood, I have the same problem but don't know how to get back into the system.  How did you do it?

---


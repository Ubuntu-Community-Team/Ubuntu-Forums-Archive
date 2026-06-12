---
title: "mplayer downloads .rpm pkg"
date: 2007-07-27
forum: General Help
---

### Post by vbdanl on 2007-07-27
Hi.  I am downloading a .rpm pkg file, and it downloads with mplayer instead of the normal download manager or whatever you call it.  what do i need to change to make mplayer not think it should be downloading the rpm files?
i went into preferences, but don't see anything with rpm extension.  several appear to have "no extension".  what program should i tell it to open .rpm packages with?
thanks.

---

### Post by dpar on 2007-07-27
I don't believe Ubuntu will 'open' an rpm. I think you have to convert it to a .deb first with alien. Don't ask me how though.:)

---

### Post by cookies on 2007-07-27
You must download the Alien package with Synaptic.

And the repositories have MPlayer. *Can't remember which though*

---

### Post by vbdanl on 2007-07-27
maybe i asked the question wrong.. i know ubuntu won't open .rpm files.  i know to use alien.  i don't know why when i try to download a rpm file, it downloads with mplayer, instead of just downloading it to my Desktop.  Sometimes I can right click after the download, and then tell it to save the file, but not always.  I just want it to download the file to my Desktop, and not use mplayer at all..  kind of like when i download a .jpg file, it just downloads it, or maybe asks if i want to save it to disk, or open it with whatever.. the rpm does not ask me that. it just starts downloading with mplayer, after it is finished, it is not put on the desktop or home dir or anywhere that i can find..

---

### Post by dpar on 2007-07-27
Ok, what are you using to download? Firefox?

---

### Post by vbdanl on 2007-07-30
Yes, I am using mozilla firefox as my browser.  the downloads are initiated through it by going to the website, then selecting the download link.  some files download as expected, like jpg's (it asks me if i want to run the program or save it to disk).

---

### Post by TKR101010 on 2007-08-05
I understand. Here's what you want to do. In Firefox, follow this path ...

Edit menu => Preferences => Content tab => File Types (at bottom) => Manage

in the Manage dialog that pops up, find the entry for rpm files and change it's action to 'save to computer' :)

Then you should be all set :)

What I'd like to know is how you go about setting this for files when you double click on them. 

Enjoy,

TKR101010

---

### Post by vbdanl on 2007-08-07
i went into the manage button, but the only entry in there was "FLV".  "RPM" was not in there, and I could not find a way to add entries.  It would let me update existing entries, but not add.  any ideas on how to do that?  
also, i don't know the answer to your question.. hope someone else does.
thanks.

---


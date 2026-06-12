---
title: "How can I explore a folder?"
date: 2006-07-29
forum: General Help
---

### Post by Roasted on 2006-07-29
Yeah, probably sounds like a dumb question. But I just realized I didn't know how to explore a folder.

In windows, you'd go to program files, aim, sounds, and find the sound file that you want.

Here, I'm unsure of what to do. How can I track down the sounds folder in my aim folder (well, gaim here) to find what sound files are available to use?

---

### Post by scxtt on 2006-07-29
looks like there are a few in /usr/share/sounds/gaim:
[indent]:> slocate sounds | grep gaim
/usr/share/sounds/gaim
/usr/share/sounds/gaim/redalert.wav
/usr/share/sounds/gaim/arrive.wav
/usr/share/sounds/gaim/leave.wav
/usr/share/sounds/gaim/receive.wav
/usr/share/sounds/gaim/send.wav[/indent]but you can use any sound file in gaim, assuming it's format is supported {maybe only wavs work} ...

---

### Post by bukwirm on 2006-07-29
The fastest way to get a file browser is to click Places -> Home. This opens Nautalis (the file browser) showing your home directory.
To see the gaim folder, you will need to click View -> Show hidden files. The gaim folder is called .gaim

The folder that actually contains the sounds might be somewhere else, though.

---

### Post by Roasted on 2006-07-29
> **scxtt said:**
> looks like there are a few in /usr/share/sounds/gaim:
[indent]:> slocate sounds | grep gaim
/usr/share/sounds/gaim
/usr/share/sounds/gaim/redalert.wav
/usr/share/sounds/gaim/arrive.wav
/usr/share/sounds/gaim/leave.wav
/usr/share/sounds/gaim/receive.wav
/usr/share/sounds/gaim/send.wav[/indent]but you can use any sound file in gaim, assuming it's format is supported {maybe only wavs work} ...


How'd you know that? See, this is what confuses me. I had NO clue and still have NO clue over why you'd know to go to the USR folder. *shrugs* 

But I did search and find them, though the sounds that are here aren't what I wanted. Earlier, I set up a buddy pounce and it had this really cool alert sound. It's no longer here, I don't know why. :(

bukwirm - Thanks. That works too!

---

### Post by bukwirm on 2006-07-29
Files used by applications are often in the /usr directory. 
For help finding things in the file system, look up the commands grep, find, locate.

---

### Post by scxtt on 2006-07-29
all i can say is that, to a degree, you just have to get used to how linux does things (it's not right, it's not wrong - it just is) - there's a learning curve for everything computer related ... one command i use ALL THE TIME is **slocate** (just remember to rebuild the database w/ **sudo slocate -u**) -- that way i can find anything i'm looking for by name, for at the very least, narrowing things down ...

---

### Post by Roasted on 2006-07-29
> **bukwirm said:**
> Files used by applications are often in the /usr directory. 
For help finding things in the file system, look up the commands grep, find, locate.

Something like

"grep --help" in the terminal? :confused:

---

### Post by scxtt on 2006-07-29
that works, but more like **man grep, man slocate, man find** ... this will give you {generally} detailed info about the command and even usage examples ...

---


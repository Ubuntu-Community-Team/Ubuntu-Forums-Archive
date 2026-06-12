---
title: "programs"
date: 2008-03-06
forum: General Help
---

### Post by notesetter on 2008-03-06
I'm new to Linux and a longtime Windows user. Under Windows, programs are all kept in the Programs folder.  Is there a central location in the Linux file system that I should put my programs? What should I do to keep my home folder tidy?

Thanks,

Dave

---

### Post by amingv on 2008-03-07
When you install new programs, you can usually find them in /bin or /usr/bin (they're usually placed there by whatever installation method you use).

If you're a programmer, and make some programs/scripts for yourself, it is recommendable not to put them in these folders, but to make a bin folder in your home directory (/home/user/bin) and place them there. (You can also make it .bin [/home/user/.bin] so that it remains hidden and doesn't bother you).

---

### Post by steveneddy on 2008-03-07
[This guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy") may help you a little.

When you install a program in Linux, it usually installs to the folders that it needs to go in.

Usually /usr/bin is where the "executable" goes, but the libraries and other types of relates files are scattered throughout the system.

You can install through Synaptic

System --> Administration --> Synaptic Package Manager

or in Terminal via apt-get

Or you can compile from source, but that's another thread, maybe.

---


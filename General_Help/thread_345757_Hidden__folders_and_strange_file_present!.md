---
title: "Hidden / folders and strange file present!"
date: 2007-01-24
forum: General Help
---

### Post by kvonb on 2007-01-24
I noticed recently that when I ran Nautilus and tried to browse the entire filesystem, ie the / folder, there was hardly anything there!

OK, not a problem, just use a gksu nautilus, still not there!

Very odd!

Then I turn on "show hidden files" and hey presto, everything is there again, plus a very odd file called ".hidden" which contains the names of the folders that are not shown until I show hidden files!

(see attachment)

Nothing wrong with that per say, but how the hell did it get there?  I've never seen this file before, and haven't had this hidden behaviour either!

Any ideas?

Regards, KEv :)

---

### Post by taurus on 2007-01-24
Applications -> Accessories -> Terminal
```
ls -la /
```

---

### Post by AndyCooll on 2007-01-24
Configuration/settings files are stored in your home folder and hidden by default. THe latest version of Ubuntu also hides most of the filesystem by default too. CTRL+H will reveal them. 

:cool:

---

### Post by Happy_Man on 2007-01-24
Hehe, yeah, I got freaked out by this too until i did ctrl+h. Almost had a heart attack! :) But then I realized the thing wouldn't have booted unless those files were there, so I'm ok now. I find this helps a lot for management, as there aren't all these unwieldy files that a new user wouldn't know about. Just the basics. Good job nautilus/ubuntu/whoever did this!

---

### Post by kvonb on 2007-01-25
Yes I know how to unhide files, the point I was trying to make is that this has NEVER happened in ANY other Ubuntu distro, and for that matter any other Linux/Unix distro that I have ever used!

It only started happening a few weeks ago, that is why I was concerned :).

I guess it came as part of an update, as long as it's now "normal" behaviour, all is good.

I'm not a fan of things changing without me knowing about them, I deleted the file and all is back to normal (for now!).

Thanks, Kev :)

---

### Post by kalikiana on 2007-01-25
I don't have such a file in Xubuntu - and I'm really glad.

How is any new user supposed to learn anything about linux if he can't even see such important folders? Write access is enabled for root only anyway, so that could actually break my love for Ubunutu. :/

---

### Post by ardchoille42 on 2007-01-25
I have no hidden files or folders in "/" and I don't remember ever seeing hidden files/folders there on Ubuntu Dapper.

---


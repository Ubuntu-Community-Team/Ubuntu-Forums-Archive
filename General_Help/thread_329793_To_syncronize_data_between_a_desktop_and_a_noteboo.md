---
title: "To syncronize data between a desktop and a notebook"
date: 2007-01-02
forum: General Help
---

### Post by feryllt on 2007-01-02
Good morning to everybody,
I have two computers, a desktop and a notebook. I work on the desktop but when I am in trip I use the notebook. The problem is to maintain syncronized some sub-directories of my home among the two computers. Particularly I want that such synchronization was made when the notebook is connected to the local net. My matter is the following: would you know how to point out me as to be able to do this? Which systems of synchronization can I use?

Thanks to all...

---

### Post by Rhubarb on 2007-01-02
It seems you might need to make up your own bash script to do this.
Alas I'm not proficient enough to help you out with this, but you'd need to compare files and folders, if a file is newer than copy that one over.
I would suggest you have a good look at the man pages, especially for the "cp" command.

You'll obviously need to share your documents folder on your PC and laptop if you haven't done so already.

You may have to use ssh to get this working too, on the server type in:-
```
apt-get install ssh
```
Then to ssh into the server from a client just type in:
```
ssh username@insert.ip.address.here
```

There should be a utility somewhere on the net to automate all this synchronization for you.

---

### Post by tweedledee on 2007-01-06
> **feryllt said:**
> Good morning to everybody,
I have two computers, a desktop and a notebook. I work on the desktop but when I am in trip I use the notebook. The problem is to maintain syncronized some sub-directories of my home among the two computers. Particularly I want that such synchronization was made when the notebook is connected to the local net. My matter is the following: would you know how to point out me as to be able to do this? Which systems of synchronization can I use?

Thanks to all...

You could try to set up rsync, grsync, or Unison to do these tasks, but frankly I've found them to be a pain and fairly slow for a simple sync.  While you may have less success getting them fully automated, I'd suggest looking at one of the following Java programs (you can get them all from sourceforge, just Google the names):
fullsync
capivara
jfilesync

Personally I use the last for this purpose, even though it no longer is actively developed, because it allows me to set a time window for how close files need to be to have the "same" time (I find my desktop and laptop are sometimes different by a second or two, and most programs then want to resync a bunch of identical files).

---


---
title: "Screwed something up"
date: 2007-09-19
forum: General Help
---

### Post by culmor30 on 2007-09-19
Yeah... I went into my root account and changed some permissions or something, and now some stuff doesn't work in Ubuntu. I tried resetting everything I changed; permissions to hard drives, but it didn't work. When I log in from any of my 2 users (including root), i get some error about some file and how themes and some other settings cannot be saved.

This is also causing other problems, but my question is, can I reset Ubuntu to the default settings and permissions without reformatting/reinstalling? I actually had to wait for [SIZE="1"]windows[/SIZE] to load before I could post this. PLEASE SAVE ME!

And yes, I can still login to Ubuntu. Just no internet.

---

### Post by prince_niceguy on 2007-09-19
can you post what errors are coming???

you can use the live cd or ext3fs or something to load linux partitions... without error messages it would be difficult to help....

---

### Post by culmor30 on 2007-09-19
Not immediately, but I'll get back to you in a while. Gotta finish my civics project :P

All I remember is something about a configuration file being screwed up, therefore themes and some other settings could not be saved. I'll get back to you in a while.

And... I'll try copying the degraded file from a cd boot. Thanks for the help.

---

### Post by culmor30 on 2007-10-18
Sorry for slow reply, but I got the error:

User's $HOME/.dmrc file is being ignored. This means that ... (some other stuff about saving changes and that saving them will not be possible)

If you can still help, please do. :confused:

---

### Post by DagMan on 2007-10-18
If it's the file permisions, try this  where 'username' is your username
```
sudo chmod 600 /home/username/.dmrc
sudo chown username:username /home/username/.dmrc
```

---

### Post by culmor30 on 2007-10-18
Alright, I'm in windows (ugh) right now... I'll boot to Linux and try that. The only thing is yesterday when I tried a sudo command it yelled at me about the /etc/sudoers chmod being something it shouldn't be.

Will post from Ubuntu... hang on.

---

### Post by culmor30 on 2007-10-18
Yep, same problem:

> cullin@cullin-laptop:~$ sudo chmod 600 /home/cullin/.dmrc
sudo: /etc/sudoers is mode 0446, should be 0440

Any fix?

(I have no idea how ANY of this happened, i changed the permissions of my internal drive.... Ubuntu is on my EXternal drive.)

I have no important stuff on Ubuntu... if wiping the partition and reinstalling Ubuntu is easier, I'll go for that.

---

### Post by DagMan on 2007-10-18
well it looks like the file permissions of sudoers is messed up.  I don't know if that's going to effect the current problem, but the above error.. not sure if it stopped the chmod and chown from working.  You can try those on your user without sudo as well by the way.  To fix the sudo error though try this
```
sudo chmod 440 /etc/sudoers
```but if it is causing a problem then it might not work. in which case you can try  recovery mode and 
```
chmod 440 /etc/sudoers
```
or maybe 
```
sudo chmod 440 /etc/sudoers
```
or maybe log in as root in recovery mode if it lets you and 
```
chmod 440 /etc/sudoers
```
I've never used recovery mode as you might be able to tell

Alternatively, boot into a live cd and mount the partition where the /etc folder is
```
sudo mount /dev/something /mnt
sudo chmod 440 /mnt/etc/sudoers
```
where something is the proper drive and partition in the /dev filesystem

---

### Post by culmor30 on 2007-10-31
Sorry I have been inactive for a while. Thanks much though, I'll try those out. I did try the first one, same error.

Will post from Windows (bleh) with results :D

---

### Post by culmor30 on 2007-10-31
Okay... nothing is working. Tried it all. I got sudo to work again, but when I chmodded everything it just keeps giving me that error.

Which brings me to the decision to uninstall/reinstall ubuntu. I have nothing special saved on its partition of my ext hard drive, so I can just wipe it.

So, how would I wipe ONLY the ubuntu partition of my external HD (don't care if I have to do it from Windows) and reinstall Ubuntu to that same 90GB partition?

---


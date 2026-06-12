---
title: "No permission to write to folder"
date: 2007-11-14
forum: General Help
---

### Post by rgfrancis on 2007-11-14
Hello,
I am very new to Ubuntu so bare with me. Why is it when I try to copy some files over to the  /var/www folder it tells me I dont have permission to write to this folder?

---

### Post by perlluver on 2007-11-14
run it as with root permissions.

---

### Post by taurus on 2007-11-14
```
gksudo nautilus
```
And just drag 'n drop whatever you want to /var/www.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rgfrancis on 2007-11-14
Ok, I opened up terminal and typed "gksudo nautilus". The root-file broswer box opened. I still can't just drag 'n drop whatever you want to /var/www.

---

### Post by rgfrancis on 2007-11-14
This is what it returned:

rgfrancis@rgfrancis-desktop:~$ gksudo nautilus

(nautilus:21665): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified  are supported and host-based authentication failed.
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver return ed error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned er ror: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned err or: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

rgfrancis@rgfrancis-desktop:~$

---

### Post by rgfrancis on 2007-11-14
bump

---

### Post by PeterJS on 2007-11-14
The reason that you can't just copy the files over is the unix file permission system. /var/www is owned by root or apache, the default permission is owner can read and write all other users can only read. Which is why your user account can't just copies the file straight over.

What gksudo does is run the given program with elevated (root) security privilages that would be allowed to write to /var/www/. So that's what's going on and why people were suggesting using gksudo. As to why it's failing I can't tell you that.

If you really are desperate to get files over there right now, you use the sudo (the command line program that gksudo is based on) and cp (copy) commands to move files.

---

### Post by rgfrancis on 2007-11-14
Thanks pterjs :)

---

### Post by Necromantis on 2007-11-14
in terminal:
sudo chmod o=rwx /var/www -R

then copy your files over and when you are done:
sudo chmod o=x /var/www -R

that should do it ;)

---

### Post by decoherence on 2007-12-05
A better behavior for Nautilus would be for it to prompt you for your password, then do the copy with root privs (really no different than gksudo-ing nautilus but much more streamlined)

I'll submit the suggestion to the GNOME folks or see about doing it myself.

---

### Post by mcduck on 2007-12-05
> **rgfrancis said:**
> Ok, I opened up terminal and typed "gksudo nautilus". The root-file broswer box opened. I still can't just drag 'n drop whatever you want to /var/www.

Both the source window where you are copying from, and the window (with /var/www opne) where you are copying to need to be opened as root. So, after running 'gksudo nautilus' to open the file manager as root, go to File/Open New Window to open another Nautilus window.

I recommend also setting the window background of root's Nautilus to red or something so you don't ever accidentally mix it with Nautilus running as your own user. (You can do that in Edit/Backgrounds and Emblems).

Edit. I have myself just decided to link the Public directories inside users home dirs into /var/www, allowing every user to easily put files into their own Public directories and then access them with address localhost/username. For example, 'sudo ln -s /home/mcduck/Public /var/www/mcduck' will create the link for user 'mcduck'.

---

### Post by atlien on 2008-01-25
Thanks for everyone who put time into this thread.  As a novice it is difficult to follow Ubuntu suggestions and explanations.  For instance, someone suggested a string of code to put into terminal before copying the files.  This assumes knowledge of how to copy properly.  Dragging and dropping isn't what is being alluded to.  What is?

For novices like myself, instructions often need to be basic.  Once I know what to do I can do it, but I think veterans often forget about all of the assumptions inside the tips.  I am looking forward to gaining more knowledge so that I can in turn assist others based on my experience of needing detailed and precise explanations, which are unfortunately quite rare.  The time put into sharing makes it clear that the intentions are there but without details and precision it is often not useful for me.  I don't know about others.

---


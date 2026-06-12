---
title: "Sharing Homespace with multiple distributions"
date: 2006-09-13
forum: General Help
---

### Post by beef623 on 2006-09-13
Here's my problem, I have a test box in my office with Fedora and Ubuntu installed on it, I have each installed to their own partition but they share the swap space and I'm trying to get them to share the same partition for their /home space. Right now I have the same username set up with both distributions and here is the error message I get from Ubuntu when I try to log on:
> User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
I'm still learning my way around the console so I may just be typing my commands in wrong but do you guys thing this is something that could even work? or am I just wasting my time trying...

---

### Post by BoHu on 2006-09-13
I have tried this before with several different distros. Sometimes it works, sometimes it doesn't. I really don't know why.

That's all the help I can give you. Maybe someone else knows more?

---

### Post by beef623 on 2006-09-19
Thanks though.

Ok I got the above bug worked out by tying the two users together and now I'm getting the same error message from Fedora and Ubuntu so I think I'm getting closer. Here's the new error message (it appears after name/password is entered).

Your session only lasted less than 10 seconds blah blah...View details:

> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/gdm/:0.Xservers" -h "" -1 ":0" "beef"
-/bin/bash: /home/beef/.bash_profile: Permission denied

(gnome-session:2423): libgnomeevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/beef/.gnome2/': Permission denied


Any help would be appreciated.

---

### Post by PriceChild on 2006-09-19
I don't advise sharing the same home partition because this is where many program settings are stored.

DIfferent distros have different versions of programs with sometimes different style config files.

It may work, it may not, it may be somewhere inbetween.

Pricey

---

### Post by beef623 on 2006-09-19
Thanks for the quick response. I think I can live with that, do you think I will run into any trouble using the same user with both distros?

I guess I should ask if I'm doing what I think I am. I went to the /etc/passwd file for both and set the user id to the same number. Will that let me share that user's permissions between the two?

---


---
title: "Argh! New to Linux and about to cry .dmrc and .ICEauthority"
date: 2007-10-02
forum: General Help
---

### Post by Searid on 2007-10-02
I apologize if this has been answered before, but I tried what was suggested on [this]("http://ubuntuforums.org/showthread.php?p=2619991#post2619991") thread and that didn't seem to work. The,"chmod et. Al." Seriously, if I wasn't so stoic, I'd cry.

So, as near as I can tell, the problem was installing Pando with WineX, which doesn't really make much sense ... but, whatever. After restarting after that, I can no longer log in. On the first screen I get:

> User's $HOME/.dmrc file is being ignored. This prevents the default session and language rom being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.

then! I was getting some error message about .ICEauthority and how I didn't have access, but after using the fix in that thread, now I get a message saying my login lasted less than ten seconds, ... the error message is:

> /etc/gdm/PreSession/Default: Registering your session wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:O.Xservers' -h "" -l ":O" "searid"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 20: [[: not found

( gnome-session:5664) : libgnomevfs -WARNING **: Unable to create ~/.gnome2 directory: Premission denied
Could not create peruser gnome configuration directory '/home/searid/.gnome2/': Permission denied

Now, reading that, I managed to get confused and wound up staring off ino space for a bit, but than I figured I'd try logging in with Failsafe GNOME ... so, after the initial denial of the .dmrc, I'm given another error message from (~/.xsession-errors file)

Joy. Now, Failsafe Terminal ...  I get the .dmrc error again, and, this is new to the changes made with the chmod:

> bash: /home/searid/.bashrc: Permission denied

I'm sorry if I've given too much information, or not enough - but I'm about to break down. Unfortunately, just reinstaling Ubuntu isn't really an option, because since switching to Linux, no media will mount in my CD-ROM (I've tried two seperate ones) ... I can burn things, just not mount. Unrelated though. Anywho ... any help would be very much appreciated. I'm new; and ignorant. Yay.

---

### Post by p_quarles on 2007-10-02
When you say you can't mount any CDs, do you mean from within the operating system? Have you tried booting from a CD? 

I ask just because the only solutions I know of to this kind of problem are A) reinstalling, and B) using a recovery disk to fix the system. If you can't boot from a CD, the problem is very likely with the CD drive itself, and I'm guessing that the only solution is to repair or replace it.

---

### Post by bodhi.zazen on 2007-10-02
sounds as if the ownership or permissions of /home are off

You can try booting to the recovery mode. This will be a command line interface.

You can start gnome with :

```
gnome-session
```

Now check the ownership and permissions of your /home/user_name

should be owned by the user and permissions 770 will do just fine ... So assuming your log-in name is "searid"

```
chown -R serid.serid /home/serid
chmod 770 /home/serid
```

You can also try creating a new user, be sure to give the new user administrative access so you can sudo.

Reboot

---

### Post by Searid on 2007-10-02
Woo! Yeah, I logged in as root in recovery mde and loaded with

> startx

but for some reason I couldn't access Users and Groups, it gave me an error. However! I did what you suggested, and it worked.w00t. I'm still getting an error for the .dmrc, but now I can log in at least.

At this point, it's the little victories. Any idea why I'd still be getting the .dmrc error?

As for the CD-ROM, it's rather curious, because it'll work in another computer I have, just not this one. Not sure ... not an issue anymore. I'll fix that later, at least now I can log in.

Thank you so much!

---

### Post by bodhi.zazen on 2007-10-02
Well I assume you somehow changed the permissions of your home directory

Must have been more then that if you are still getting an error, so :

.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

---

### Post by Searid on 2007-10-03
Woo-hoo! That worked! Thank you so much, I think I just wet myself a little out of happiness. You're freakin' awesome. *dances*

---


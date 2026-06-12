---
title: "Your Session only lasted less than 10 seconds..."
date: 2007-08-21
forum: General Help
---

### Post by Abominable_Bathtub on 2007-08-21
Logging in with default GNOME displays this message. Logging in with failsafe GNOME displays this 'Your session only lasted less than 10 seconds...'. I can still login to terminal if i do ctrl+alt+F1.

.xsession-errors file
> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "quentin"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/xmodmap: unable to open file 'usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap: 1 error encountered, aborting.
Could not get password database information for UID of current process: User "???: unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
EOF in dbus-launch reading address from bus daemon



As far as I know, I didn't do anything untoward the last time I used it, besides setting a password for root that was not needed.

---

### Post by Abominable_Bathtub on 2007-08-22
Anyone?

---

### Post by davidjmayo on 2007-08-22
see

[http://ubuntuforums.org/showthread.php?t=512736&highlight=Your+Session+only+lasted+less+than+10+seconds](http://ubuntuforums.org/showthread.php?t=512736&highlight=Your+Session+only+lasted+less+than+10+seconds)

---

### Post by julian67 on 2007-08-22
> **Abominable_Bathtub said:**
> 
As far as I know, I didn't do anything untoward the last time I used it, besides setting a password for root that was not needed.

That would probably be the cause of the problem. You might have broken sudo when you did this, I would search here/google for answers based on this premise. This might help: [how to recover sudo]("http://www.psychocats.net/ubuntu/sudo")

also see 

[http://ubuntuforums.org/showthread.php?t=16655]("http://ubuntuforums.org/showthread.php?t=16655")

where you'll see other people have managed to get in the exact same situation. 

I think you'll be able to get everything back to normal.

---

### Post by MotHaiBa on 2007-08-26
Hi all, I am also getting a similar error when I login. The error message I am getting is:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "chau"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: No space left on device

I am pretty sure that I have plenty of space left on my HD.

Could you please help?

Thanks in advance.

---

### Post by MotHaiBa on 2007-08-26
Fixed it, using the command 'sudo apt-get clean' posted by Aysiu.

[http://ubuntuforums.org/showthread.php?t=521803&highlight=session+lasted+10+seconds](http://ubuntuforums.org/showthread.php?t=521803&highlight=session+lasted+10+seconds)

Thank you.

---


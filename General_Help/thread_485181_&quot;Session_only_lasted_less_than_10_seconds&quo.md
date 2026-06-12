---
title: "&quot;Session only lasted less than 10 seconds&quot; error when logging into gnome"
date: 2007-06-26
forum: General Help
---

### Post by obscenic on 2007-06-26
I've moved this, as I though perhaps absolute beginner talk might not be the best place for 
this thread - I kinda sorta know my way around linux.

I've had feisty up and running smoothly for a couple of weeks, and the only recent change I've made was installing gnomebaker as far as I can recall. Just before the first time this happened, I was in a state where no gnome apps would start up and the system locked during reboot and I was forced to do a hard resart.

Now I get the "Your session only lasted less than 10 seconds" error after logging into gnome.

my .xsession-errors file reads something like this:

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mark"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: 128: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 129: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 147: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: 211: cannot create /dev/null: Permission denied
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
gnome-terminal: error while loading shared libraries: libutil.so.1: cannot dynamically load executable


I've tried the forum suggestions such as re-chowning the .ICEauthority file, renaming the Xsession file, checked the hard drive space (18gb free), all to no avail. I'm totally lost. Any help would be greatly appreciated.

Should add that I seem to get similar messages when logging into tty1: -bash: /dev/null: Permission denied" in a seemingly endless loop...

---

### Post by scrooge_74 on 2007-06-26
can you creat another user and log normally?  You probably have some file in your home directory that got corrupted, something like that once happened to me.  But I can recall what I did to fix it

---

### Post by harty83 on 2007-06-26
I've had the same happen to me.  Chowning everything in my home directory fixed it.

Either login through gdm to failsafe terminal (by clicking on sessions then failsafe terminal) or press Ctrl-Alt-F1 after getting to your gdm screen.  Then

```
sudo chown -r username.username /home/username
```

Replace username with yours.

---

### Post by harty83 on 2007-06-26
Sorry that should be a capital R not a r.

```
sudo chown -R username.username /home/username
```

---

### Post by obscenic on 2007-06-26
> **harty83 said:**
> Sorry that should be a capital R not a r.

```
sudo chown -R username.username /home/username
```

No such luck.... Any other ideas?

---

### Post by harty83 on 2007-06-26
It is possible that the read/write permissions got corrupted.  What happens if you do this:

```
sudo chmod -R u+rw /home/username
```

---

### Post by obscenic on 2007-06-26
Exact same deal... :(

---

### Post by harty83 on 2007-06-26
Mmmm.  Have a look in /var/log/gdm and see if the logs give any indication.  

```
dir /var/log/gdm
```

If you are familiar with vim or pico, you can use them to view the logs.

If not, then use pico

```
sudo pico /var/log/gdm/filename
```

Press ctrl-x to exit.

Are you using a second pc to post here or are you logged in through another user?

---

### Post by scrooge_74 on 2007-06-26
> **harty83 said:**
> I've had the same happen to me.  Chowning everything in my home directory fixed it.

Either login through gdm to failsafe terminal (by clicking on sessions then failsafe terminal) or press Ctrl-Alt-F1 after getting to your gdm screen.  Then

```
sudo chown -r username.username /home/username
```

Replace username with yours.

in the command sudo chown -R username:username /home/username   ?   " : " instead of a dot

also, I remember check that your /tmp   is write enable for  all users and executable also

That is what happend to me I somehow changed that and my user lost permissions to write to /tmp

---

### Post by harty83 on 2007-06-26
> **scrooge_74 said:**
> in the command sudo chown -R username:username /home/username   ?   " : " instead of a dot

My bad.  Sorry about that.

---

### Post by obscenic on 2007-06-27
> **scrooge_74 said:**
> in the command sudo chown -R username:username /home/username   ?   " : " instead of a dot

also, I remember check that your /tmp   is write enable for  all users and executable also

That is what happend to me I somehow changed that and my user lost permissions to write to /tmp

Yeah, I had used a colon.. and tmp was drwxrwxrwt  owned by root:root, I just 777'd it (drwxrwxrwx)  Is that all ok?



Harty - in the gdm logs, I have 5 files: :0.log, :0.log.1, :0.log.2, :0.log.3, and :0.log.4.

All appear identical and the only thing that strikes me as off is an error
"(EE) xf86OpenSerial: Cannot open deivce /dev/input/wacom
No such file or directory.
Error opening /dev/input/wacom : Success"

This appears 3 times.  Following that I have 3 font path errors, but I doubt that's causing me any grief.

Does this help?

---

### Post by obscenic on 2007-06-27
I think I should add at this time that when I've been told to boot into failsafe terminal, I have been unable to do so.  It gives me the exact same error when I try to log into gnome.  I've been ctrl-alt-1-ing to TTY1, wherein I attempt to log in, it gives me an endless loop (I think, I don't know how to go back into the buffer) of 

-bash: /dev/null: Permission denied

Which I've been escaping with ctrl+c.... this returns me to bash as my user.

> 
Are you using a second pc to post here or are you logged in through another user?

Second PC.  Creating new users does nothing...

---

### Post by obscenic on 2007-06-27
Ah. Some movement.  I chmoded /dev/null to 666 (which I think is what it ought to be for feisty, can anyone confirm?), which has cut out a all the /dev/null error lines when logging in to gnome.  Ah.  But after reboot, dev/null has re permissioned itself to 660... (rw-rw----).  Back to square one!!!!!!

---

### Post by harty83 on 2007-06-27
> **obscenic said:**
> I chmoded /dev/null to 666 (which I think is what it ought to be for feisty, can anyone confirm?)

I can confirm

```

alan@desktop:~/Desktop$ ls -n /dev/null
crw-rw-rw- 1 0 0 1, 3 2007-04-21 17:04 /dev/null

```

The wacom error is fine.  Just means you don't have a wacom tablet connected.

Try looking at your syslog, kern.log, dmesg, and any other you can think of for clues (all in /var/log).

---

### Post by Qu4k3R on 2007-06-27
Have you logged in with the "failsafe GNOME"  (or KDE) session option?
It might help you.

You might have installed something that is initiated on your session startup.
Or something is not working "correctly".

---

### Post by obscenic on 2007-06-27
> **harty83 said:**
> I can confirm

```

alan@desktop:~/Desktop$ ls -n /dev/null
crw-rw-rw- 1 0 0 1, 3 2007-04-21 17:04 /dev/null

```

The wacom error is fine.  Just means you don't have a wacom tablet connected.

Try looking at your syslog, kern.log, dmesg, and any other you can think of for clues (all in /var/log).

Well this could be problem #1.  /dev/null resets itself to 660 on startup (crw-rw----).  Anyone know why?

[QUOTE=Qu4k3R]Have you logged in with the "failsafe GNOME" (or KDE) session option?
It might help you.

You might have installed something that is initiated on your session startup.
Or something is not working "correctly".[/QUOTE]

Nope, as per my previous message, the only way I can get any access to my system is by using TTY1 and hitting ctrl+C during the dev/null errors.  No gnome, no failsafe gnome, no failsafe terminal, no GDM in recovery mode either,

---


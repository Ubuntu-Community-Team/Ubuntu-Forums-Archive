---
title: "Hmm, Ubuntu just comitted suicide or something"
date: 2004-11-08
forum: General Help
---

### Post by negativ on 2004-11-08
Earlier today, everything was working fine.

Then, I used Synaptic to install k3b (and all its necessary dependency packages).

Then I booted into WinXP to play Vice City for a while.

Just now, I tried to boot back into Ubuntu and was greeted by this after entering my username & password:

"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe options to see if you can fix this problem."

Viewing details yields this:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u "/var/lib/gdm/:0.Xservers" -h " " -l ":0" "negativ"

** (gnome-session:4346): WARNING **: unable to read ICE authority file: /home/negativ/.ICEauthority


....

So.... uhh.... wtf?    :sad:  :-k  #-o  :confused:

---

### Post by FX on 2004-11-08
I had that problem also. I just opened a fail-safe term from the log in screen and did a "sudo chown user:user ~/.ICEauthority" and then it worked.

FX

---

### Post by negativ on 2004-11-08
Cool, that did the trick.  Sure wish I had a clue as to wtf happened, though.   :-k  :-k

---

### Post by wallijonn on 2004-11-08
[QUOTE=FX]I just opened a fail-safe term from the log in screen and did a "sudo chown user:user ~/.ICEauthority" and then it worked.[/QUOTE]

"Just"?

How did you open a "fail-safe terminal"? How is that different from a "root terminal"?

```
sudo chown user:user ~/.ICEauthority
```

What a great tip. 

 =D> (2 hands clapping)

---

### Post by FLeiXiuS on 2004-11-09
[QUOTE=wallijonn]"Just"?

How did you open a "fail-safe terminal"? How is that different from a "root terminal"?

```
sudo chown user:user ~/.ICEauthority
```

What a great tip. 

 =D> (2 hands clapping)[/QUOTE]

Failsafe = Runlevel 1
Root = Runlevel 2-5

---

### Post by Rancoras on 2004-11-09
[QUOTE=negativ]Cool, that did the trick.  Sure wish I had a clue as to wtf happened, though.   :-k  :-k[/QUOTE]

The "what happened" is outlined here:

[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988)

---

### Post by Julius on 2004-11-09
I have k3b installed and I didn't have that problem. Anyway I have to open k3b as root (otherwise it wont recognize any cd writers) and fonts look crappy :P

At least it can write cds ;)

---

### Post by FX on 2004-11-09
Also at the login screen where you can pick different sessions (gnome,kde,xfce) you have the option there of also picking fail-safe gnome and fail-safe terminal.

FX

---

### Post by krietor on 2004-11-10
k3b is working for me finally.. Now it runs and burns, but only when I run it as root, and then won't exit cleanly.
When I start it, here's the beginning of a super-long output of errors, mostly about missing icons.!? . .:
carbuncle:/home/me# k3b
QPixmap: Cannot create a QPixmap when no GUI is being used
QPixmap: Cannot create a QPixmap when no GUI is being used
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 20x20/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 48x48/filesystems not valid.
kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/Crux/ group 48x48/emblems not valid.
---Also there are a few of these .:
k3b: WARNING: KGenericFactory: instance requested but no instance name passed to the constructor!

---It goes on about the missing icons for a while, and then K3b boots up and seems to work like a charm. I burned some music CD's.
Then when I go to exit K3b Here's what I get.. .:
k3b: ERROR: (K3bSongManager) Can't open file /root/.kde/share/apps/k3b/songlist.xml
carbuncle:/home/me# {It pauses here for a moment, and then:} Mutex destroy failure: Device or resource busy
ICE default IO error handler doing an exit(), pid = 4033, errno = 0
And then no more response, ...?
 I wonder if there's a package I'm missing that is a sort of dependency of K3b's?
Or is it to do with ICEauthority?

---


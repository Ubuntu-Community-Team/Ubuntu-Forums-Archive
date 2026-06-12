---
title: "Installed fine - but brown screen, white cursor and that's it!"
date: 2005-10-17
forum: General Help
---

### Post by puppy on 2005-10-17
Hi folks, Breezy Badger installed fine but when I log in it just goes to a brown screen with a (moveable) white cursor (this is exactly the same problem I had when installing Hoary - thought they would have fixed this with the new distro :( ). Anyone got any ideas how I can fix it and get to the desktop?

Cheers

---

### Post by paul2005 on 2005-10-17
I've been using Breezy for a few days now with no problems, then all of a sudden this evening after rebooting I can't log in to the desktop at all. When I enter my username and password the screen goes brown for about 20 seconds, then just goes back to the logon screen, a bit like the comment above. I wasn't doing anything special before I rebooted so I don't know what's gone wrong. I can log in to a terminal prompt but no GUI.

Any ideas?

---

### Post by aclaunch on 2005-10-17
Try Alt-Ctl-F1 and log in in terminal mode. From here you can run apt, review your config settings, etc. It sounds like gnome is not initializing for some reason-were there problems during the install?

To get back to a graphical environment Alt-Ctl-F7

Good Luck
Alan

---

### Post by Murgle on 2005-10-17
you could also try typing 'cat /var/log/Xorg.0.log' at the command prompt then and see if it gives you any errors.

---

### Post by moopere on 2005-10-18
[QUOTE=paul2005]I've been using Breezy for a few days now with no problems, then all of a sudden this evening after rebooting I can't log in to the desktop at all. When I enter my username and password the screen goes brown for about 20 seconds, then just goes back to the logon screen, a bit like the comment above. I wasn't doing anything special before I rebooted so I don't know what's gone wrong. I can log in to a terminal prompt but no GUI.

Any ideas?[/QUOTE]

Do you hear the login ubuntu sound? 

I have a problem like this with one of my machines, been like it since hoary - ESD is choking at login time.  You might have a similar problem to me if your login looks like this:

1) Turn on machine, after booting GDM starts and the 'drums' sound

2) You login, are authenticated with no problem, the login screen dissapears, the gnome splash screen appears, and the ubuntu startup sound starts

3) The startup sound abruptly stops (just before the end) and the gnome splash screen goes away - you are left with a white cursor on a brown background.

The machine has not crashed as you can switch between VT's and X - but you can't get past this point on X

If this is you, the problem is ESD.  Its hanging on something.  If you wait a half hour or so you'll get to gnome (ESD times out???).  If you can't wait that long then switch to a VT "killall esd".  You will then find that the gnome desktop on VT7 completes _and_ you'll still have gnome desktop sounds etc - everything will be normal.

Note that if you switch to polypaudio you won't get this problem (you'll get a different set of serious problems ha!).

HTH,
Craig

---

### Post by paul2005 on 2005-10-18
Thanks for the suggestion, but it won't eventually go into Gnome - after about 20 seconds on the brown screen the screen goes black briefly and then just returns to the login screen.

I logged into a terminal OK and checked 'cat /var/log/Xorg.0.log' but there don't seem to be any errors there. In fact I can type 'nautilus /home/' and my desktop wallpaper appears with icons on it, and nautilus pops up fine, there just aren't any window borders.

I'm pretty new to Linux so I don't really have any ideas what could be wrong - any help would be appreciated!

---

### Post by paul2005 on 2005-10-19
Hi,

I've been looking round in lots of forums but still can't find any answer to what's wrong with my setup! There's lots of similar problems but I can't find any way to fix my problem and boot into Gnome!

I would just reinstall Ubuntu and start again but I'm a bit reluctant to do that as I may well get the same problem happening in another few days when I've set everything up again!

Has anyone got any ideas how I can fix it?!

Thanks.

---

### Post by ivanjs on 2005-10-19
[QUOTE=puppy]Hi folks, Breezy Badger installed fine but when I log in it just goes to a brown screen with a (moveable) white cursor (this is exactly the same problem I had when installing Hoary - thought they would have fixed this with the new distro :( ). Anyone got any ideas how I can fix it and get to the desktop?

Cheers[/QUOTE]
Sounds like the EXACT same problem I had when I tried to install. Saw a brown screen and my cursor, which I cold actually still move around, but nothing happened. Do you have an nvidia card? If so, try this:

As soon as you see the brown screen, hit CNTRL-ALT-F1 to jump out to the command line.
Next, use your favorite text editor (i use vi) and edit the following file:

sudo vi /etc/X11/xorg.conf

Now, find the line in xorg.conf that says "nv" and change it to "vesa", save the file, then restart.

Good luck. Worked for me!

---

### Post by chanders on 2005-10-19
By doing what the above post says, you should be able to login to GDM. If you are running a pc with an Nvidia card, you can use synaptic to install the nvidia driver and then change 'nv' in xorg.conf to 'nvidia'

---


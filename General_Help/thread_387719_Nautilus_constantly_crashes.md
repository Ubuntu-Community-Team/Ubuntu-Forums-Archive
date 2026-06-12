---
title: "Nautilus constantly crashes"
date: 2007-03-18
forum: General Help
---

### Post by Cappy on 2007-03-18
Prelude:
I had a weird problem last night, my filesystem went into read-only mode - I don't know why. I checked my logs and didn't see anything relating to this problem! 
My system was frozen at the screensaver when I came back since the filesystem was read-only and it couldn't write any temp files. I had to use a terminal to **Halt** the system. Once I rebooted I was prompted to do a manual fsck to repair the filesystem and there was a HUGE amount of files with problems.

Problem:
Now, Nautilus crashes if I open any folder or drive! I get a CD/DVD player bug-report. After I close the bug report, nautilus crashes again and gives me another bug report (over and over).

When I launch nautilus in a terminal it gives me the error 

```

** (bug-buddy:5834): WARNING **: Couldn't load icon for Open Folder

```

I thought "okay, a setting is just corrupt" so I tried moving the configuration files to a folder I named ".backup". I moved .gnome .gnome2 .kde .metacity .nautilus and I rebooted but it still crashes. I then even moved my .gconf and rebooted but that didn't fix anything either (I thought it might be a missing "open folder" icon on my theme icons or something).

I've tried cleaning apt-get and reinstalling nautilus but that doesn't help at all. I've also tried some other fixes such as "--desktop" Ive found in other threads. There doesn't seem to be a corrupt filename in my Home directory either. Running nautilus with sudo doesn't help at all:

```

cappy@cappychan:~$ sudo nautilus

(nautilus:6804): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

** (bug-buddy:6821): WARNING **: Couldn't load icon for Open Folder

```

Right now, I have nautilus uninstalled and **thunar** is working well.

Any thoughts on how to fix this nautilus problem (or the original problem where my file system became read-only .. this has happened a few times now)? :confused:

Edit: Thunar crashes if I right-click on a folder and click "emblems" - probably the problem! Not sure how to fix it

---

### Post by Cappy on 2007-03-19
Okay well .. I just have to say that today I learned a lot that I didn't know.
This was an unresolved bug on the GNOME bugzilla so I found out how to do it myself.
See my bug tracker post:

[http://bugzilla.gnome.org/show_bug.cgi?id=420017](http://bugzilla.gnome.org/show_bug.cgi?id=420017)

if you have this problem, I would just remove every "icon-theme.cache" on your system.

---


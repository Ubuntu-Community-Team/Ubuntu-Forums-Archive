---
title: "startup daemon"
date: 2004-11-06
forum: General Help
---

### Post by TravisNewman on 2004-11-06
I know how to set daemons to start at boot, and I think I've seen what I want on this forum, but I can't find it. What I'd like to know is, how do I see what will be starting up and how do I turn them off? I've got a lot of stuff that I know I don't need and some stuff that I'm not sure about, but I'd like to have a list of what's running so I can find out. The boot process goes by too fast to catch them all.

Like I said, I think this was discussed elsewhere on the forum, but I did a search with a few different search strings and I can't find anything.

---

### Post by TravisNewman on 2004-11-07
Sorry to bump, but... bump.

---

### Post by flygmaskin on 2004-11-07
Just click computer > system configuration > services

---

### Post by TravisNewman on 2004-11-07
[QUOTE=flygmaskin]Just click computer > system configuration > services[/QUOTE]
 I've double and triple checked, I most definitely don't have that menu option. It should be between screen res and synaptic, but there's most definitely nothing there.
By the way if that's your picture in your userpic, you look just like one of my former Computer Science professors.

---

### Post by flygmaskin on 2004-11-07
[QUOTE=panickedthumb]I've double and triple checked, I most definitely don't have that menu option. It should be between screen res and synaptic, but there's most definitely nothing there.
By the way if that's your picture in your userpic, you look just like one of my former Computer Science professors.[/QUOTE]
 Weird, I'm running hoary, so maybe it is a new option.

No it's not me, I just image-googled for rolf (dont ask :))

---

### Post by TravisNewman on 2004-11-07
[QUOTE=flygmaskin]Weird, I'm running hoary, so maybe it is a new option.[/QUOTE]

Nope, I'm running Hoary now. It's still not there. Does anyone else have this option?
And flygmaskin, can you tell me the command that it runs so that I can see if I have it installed, but just don't have a menu entry?

---

### Post by Wombley on 2004-11-07
Someone asked this on the mailing list. According to  [http://lists.ubuntu.com/archives/ubuntu-devel/2004-November/000999.html](http://lists.ubuntu.com/archives/ubuntu-devel/2004-November/000999.html) its been "disabled by the upstream authors for the release, because it is not currently usable." 
To answer your original question, services started at boot have symlinks in /etc/rc2.d (runlevel 2 seems to be the default for Ubunta), you can disable them by deleting the symlinks.

---

### Post by TravisNewman on 2004-11-07
[QUOTE=Wombley]Someone asked this on the mailing list. According to  [http://lists.ubuntu.com/archives/ubuntu-devel/2004-November/000999.html](http://lists.ubuntu.com/archives/ubuntu-devel/2004-November/000999.html) its been "disabled by the upstream authors for the release, because it is not currently usable." 
To answer your original question, services started at boot have symlinks in /etc/rc2.d (runlevel 2 seems to be the default for Ubunta), you can disable them by deleting the symlinks.[/QUOTE]
 Thanks, that helped :) Its much cleaner now.

---

### Post by Magneto on 2004-11-07
also try
```
sudo update-rc.d -f processname remove 
```

which is no different than manually removing the links in your /etc/rc$.d directories

---


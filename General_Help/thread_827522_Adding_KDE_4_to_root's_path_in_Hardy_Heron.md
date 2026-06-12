---
title: "Adding KDE 4 to root's path in Hardy Heron"
date: 2008-06-12
forum: General Help
---

### Post by ChameleonDave on 2008-06-12
Applications for KDE 4 are strange in that their executables are located at */usr/lib/kde4/bin*.  This path is added to the bash path for all users, except for root.

I can alter the path for root like this:
```

sudo -s
PATH=/usr/lib/kde4/bin:$PATH
```

But, it doesn't persist.  I've tried adding the path to files such as */etc/environment*, */etc/profile*, */root/.profile* and */root/.bashrc*, to no avail.

How on earth can I set the root path?

---

### Post by aysiu on 2008-06-13
Try ```
sudo -i
``` instead of *sudo -s*

---

### Post by ChameleonDave on 2008-06-14
> **aysiu said:**
> Try ```
sudo -i
``` instead of *sudo -s*
Why should that work?  I mean, whether we use "-s" or "-i" to become root, or even if we don't become root at all, the "PATH=/usr/lib/kde4/bin:$PATH" command only works for the current session.  That was my understanding of it.  It needs to be added to a config file if we want it to persist across sessions.



Nevertheless, I've decided to play with those options to see what happens.

If I become root with "sudo -s", KDE 4 applications are not in my path.

If I become root with "sudo -i" or "sudo su", KDE 4 applications are in my path, and &#8212; what's more &#8212; I get a colourful prompt (because I set the root prompt to be colourful in some config file).  It seems that "sudo -s" doesn't *really* make me root.  It's some sort of *fake* root.

This is quite interesting.  It doesn't help much though.  I don't want to have to become root with "sudo su" and then type my commands.  I want to remain a user, and just execute the individual command, Ubuntu-style, by typing "sudo *command*".  How can I make that work?  Where is sudo getting its path from?  It's neither my user path nor the root path, which both contain /usr/lib/kde4/bin.

---

### Post by aysiu on 2008-06-14
Yes, *sudo -s* logs you in as root but keeps the current shell's environment. More details [here](https://help.ubuntu.com/community/RootSudo#head-e5dd6585ff1d17e0ded49d7f947b462ac22f37c7).

I'll see what can be done about the path problem, but you can in the meantime specify the entire path: ```
kdesu /usr/lib/kde4/bin/konqueror
``` for example.

---

### Post by ChameleonDave on 2008-06-14
> **aysiu said:**
>  you can in the meantime specify the entire path: ```
kdesu /usr/lib/kde4/bin/konqueror
``` for example.

Yeah, I was doing that.

To save typing, I made a symlink that points from /kde4 to /usr/lib/kde4/bin.  But I'm looking for a solution, not a workaround.

---

### Post by aysiu on 2008-06-14
I couldn't do it.

I tried *sudo -i* and then exporting the path, but when I exited that and came back, it was gone from the path again.

I tried adding it to /root/.bashrc also to no avail.

The only successful way I've had with getting the root stuff to work is adding symlinks: ```
sudo ln -s /usr/lib/kde4/bin/kate /usr/bin/kate
sudo ln -s /usr/lib/kde4/bin/konqueror /usr/bin/konqueror
``` so that ```
kdesu kate
``` and ```
kdesu konqueror
``` will work again.

---

### Post by ChameleonDave on 2008-06-14
Thanks, but again, that's a workaround, not a solution.  Adding or removing apps will break it.

---

### Post by virtudtierra on 2008-08-12
> **aysiu said:**
> I couldn't do it.

I tried *sudo -i* and then exporting the path, but when I exited that and came back, it was gone from the path again.

I tried adding it to /root/.bashrc also to no avail.

The only successful way I've had with getting the root stuff to work is adding symlinks: ```
sudo ln -s /usr/lib/kde4/bin/kate /usr/bin/kate
sudo ln -s /usr/lib/kde4/bin/konqueror /usr/bin/konqueror
``` so that ```
kdesu kate
``` and ```
kdesu konqueror
``` will work again.

I fix the problem removing kdesudo (kde 3.x) and just installing the kdesudo-kde4 package!

enjoy it!

regards

Jorge

---


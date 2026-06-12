---
title: "Gutsy has started hanging on startup"
date: 2007-12-02
forum: General Help
---

### Post by dandelions on 2007-12-02
I upgraded from Feisty to Gutsy today, and I could log in fine for the first few times. I deleted two icons from my icon theme and did ctrl-alt-backspace to get X to refresh and inherit them from Tango instead; when I attempted to then log in, it just hung on a beige screen after I put in my username and password. I put those icons back via Windows (I dual boot with xp) but it still hangs on a beige screen rather than loading my splash screen or the desktop. I have a mouse cursor which I can move, but that's it. I've waited five minutes and nothing happens - I don't think this is the same problem lots of people are having since they only have to wait for perhaps fifty seconds for it to load.

I've also tried failsafe gnome and it still hangs. I can load a terminal, and I can access all the files on that partition via XP if things need to be edited. Does anyone have any ideas?

---

### Post by loa on 2007-12-08
Does the virtual terminals work? Ie press ctrl-alt-f[1-6], or ctr-alt-[left/right]arrowkey. If it does, you can try some commands there.

Such as:
```
sudo dpkg-reconfigure x-server
```

(or what the package name is, I dont remember now)

you can type ```
apt-get search x-server
```, or search for other packages which you can try reconfiguring.
Maybe this could help, probably not, but it's worth a try.

You could also typ
```
top
```
there to se if there is some process consuming a lot of cpu-power

---

### Post by dandelions on 2007-12-08
They didn't, though the failsafe terminal did, and I could do some things in there but not enough to fix it.

I reinstalled this morning, having formatted my linux partition, and got the exact same problem after three hours of it working fine (aside from a new glitch in which it now took five minutes to reach the login screen). The sound broke partway through, then it wouldn't log in, just like last time.

I give up on Gutsy: my experiences of it so far have been entirely negative, and I hate the idea of an operating system which works perfectly until you do something it dislikes - but it won't tell you what you did. It's like being in primary school all over again. I'm going back to Feisty, which never deleted my files when it glitched, or broke its own sound randomly, or refused to boot.

---


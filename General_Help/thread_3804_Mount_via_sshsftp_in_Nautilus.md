---
title: "Mount via ssh/sftp in Nautilus"
date: 2004-11-09
forum: General Help
---

### Post by adamvert on 2004-11-09
Hi

So I'm trying to mount a remote directory via ssh or sftp... I have various problems doing it, which I don't really understand.  If I try typing 

sftp://<user>@<machine>

or

ssh://<user>@<machine>

into the 'Go To' bar, I don't get anywhere.  If I use the 'Connect to Server' dialog (choosing ssh, sftp isn't available there), it's more likely to work.

Do other people find this functionality to be solid, or is it just still at a sketchy development stage?

And another question... even if I do successfully mount a remote directory, am I right in thinking that I can't actually access it from other programs?  That I can only get it in Nautilus or on the desktop?  

I'm a bit disappointed about all this, mounting over ssh would make my life sooooo much easier....

ta,
Adam

---

### Post by im_ka on 2004-11-09
afaik, you need to open
```
ssh://ip-adress-of-other-machine
```
in nautilus.

at least that's what i've been told on irc. i'm getting a laptop and i wanna use ssh as well.

tell me if it works ;)

---

### Post by adamvert on 2004-11-09
[QUOTE=im_ka]afaik, you need to open
```
ssh://ip-adress-of-other-machine
```
in nautilus.

at least that's what i've been told on irc. i'm getting a laptop and i wanna use ssh as well.

tell me if it works ;)[/QUOTE]
 whooops!

Looks like I spoke too soon.  It looks like the problem was just that Nautilus had crashed: as soon as I restarted Gnome, it all started working.

And now I can edit files remotely in Bluefish, and everything is good in the world :)


Adam

---


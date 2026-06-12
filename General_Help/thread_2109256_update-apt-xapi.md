---
title: "update-apt-xapi"
date: 2013-01-27
forum: General Help
---

### Post by greatsirkain on 2013-01-27
freezing:
this keeps happening to me & I told the software centre etc not to  even check for updates, I do it manually on synaptic, but it keeps  popping up and freezing my comp. 
Any way to rip this thing out  without breaking anything? Even top stops responding so it takes me like a  minute to kill it...It's annoying when you're in the middle of something.

---

### Post by vasa1 on 2013-01-27
If you run
```
dpkg --get-selections
```do you see update-apt-xapi installed? I'm using Lubuntu 12.10 and **don't see it**.
Did you, by any chance, install the _U_buntu Software Center?

---

### Post by greatsirkain on 2013-01-31
nope, it's not listed. But I do have the ubuntu software center in my program list as well as the lubuntu software center and synaptic
I originally installed ubuntu 12.04 but I didn't like some of the stuff that was packaged with it so I installed some lubuntu  bits and pieces, changed to the LXDE and removed the ubuntu stuff I didn't want.

 It wasn't supposed to be a permanent set up I was just trying to rescue the encrypted home folder from the last set up when all of my partitions got deleted but now I've got that much data it would be very time consuming to save/move reinstall everything so I've just been trying to patch it up as best I can :S

I do have these:
```
update-inetd                    install
update-manager                    install
update-manager-core                install
update-notifier                    install
update-notifier-common 
```

---

### Post by vasa1 on 2013-01-31
Okay, so you started off with Ubuntu. I got confused and that's why I asked. I had noticed this activity and asked about it here: [Is 100% CPU usage harmful while update-apt-xapi runs?]("http://askubuntu.com/q/79481/25656").
Then, based on the responses I got, I just decided to let it get on with its job. Now, of course, it isn't relevant to me because Lubuntu doesn't have it (yet).

---

### Post by vasa1 on 2013-01-31
> **greatsirkain said:**
> nope, it's not listed. ...
Sorry. I think it's this: apt-xapian-index.

Here's what ```
apt-get -s install software-center
``` would pull in if one tries to go the other way and install it in Lubuntu:
```
The following extra packages will be installed:
  apt-xapian-index gir1.2-gmenu-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-soup-2.4 gir1.2-webkit-3.0 laptop-detect libfile-copy-recursive-perl
  libgeoclue0 libgnome-menu-3-0 libjavascriptcoregtk-3.0-0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common oneconf python-debtagshw python-dirspec python-gst0.10
  python-oauth python-openssl python-pam python-piston-mini-client python-serial python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-xapian python-zope.interface sane-utils sessioninstaller software-center-aptdaemon-plugins ubuntu-sso-client update-inetd

```
The list may be longer because I've installed other software on my Lubuntu and so it isn't "vanilla" anymore!

---

### Post by greatsirkain on 2013-02-01
I got impatient and removed ubuntu softwre center and update manager, nothing exploded so I'm thinking it's okay :P

---


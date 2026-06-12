---
title: "A question on BitTorrent and Tor"
date: 2006-07-27
forum: General Help
---

### Post by Sagotis on 2006-07-27
Hi all,

I have a question on BitTorrent and Tor. It seems that torrent trackers can be redirected though Tor (note that tracker though Tor is different from d/l torrent file within Tor and this latter is frowned upon by the Tor community).

The command to issue this ability is found on the howto Torify page ([http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO#head-de861b050ee8ceb1e439200313f024f09d698c52](http://wiki.noreply.org/noreply/TheOnionRouter/TorifyHOWTO#head-de861b050ee8ceb1e439200313f024f09d698c52)). 

However, the command: btlaunchmanycurses --tracker-proxy 127.0.0.1:8118 <directory> (i used /tmp as the dir) does not seem to work or not seem to be supported by BitTorrent.

Why? Because given the fact that when this command (btlaunchmanycurses --tracker-proxy 127.0.0.1:8118 <directory>) is issued, either as user or by sudo the term states, error: unknown key --tracker-proxy
run with no args for parameter explanations.

Issueing the command: btlaunchmanycurses shows no option to make tracker go through a proxy.

[B]So, I guess my question is, in light of this, how can one Torify the tracker?
[/B]
Any help would be appreciated, 

Sagotis

---

### Post by Sagotis on 2006-07-28
I would like to **Bump** this for an answer!

Thanks,

Sagotis

---

### Post by sktx on 2006-10-05
What kind of error message are you getting ?

---

### Post by jonatan84 on 2008-05-05
The problem with the command suggested is that it promts for the <directory> at the end of the command. For the version Ubuntu uses, it should be something like:

btlaunchmanycurses <directory> --tracker_proxy 127.0.0.1:8118

---


---
title: "alt program to play realplayer streams"
date: 2007-02-25
forum: General Help
---

### Post by PetePete on 2007-02-25
when ever i try and play realplayer streams in firefox , it makes firefox become veeeery slow.
and when i use realplayer the program becomes very slow to respond.

is there an alternative program which I can use to play realplayer streams (.ram)

---

### Post by energiya on 2007-02-25
try MPlayer and the mplayer firefox plugin. You can find them in the repository, and I think it plays realplayer format as well (damn, it plays anything I throw on it).

**edit:** things have changed since the last time I used Ubuntu. It seems more complicated to install mplayer. See [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Mplayer32_with_Plugin_for_Firefox32").
**edit2:** or [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox"). Now I'm confused.

---

### Post by PetePete on 2007-02-25
cheeers
but i dont want to play the streams in firefox... just want a program to play them externaly.

i tried mplayer and it came up wtih the error;
"could not resolve name for AF_INET6: www.bbc.co.uk"

(was trying to play a stream from bbc's radio)

---

### Post by PetePete on 2007-02-25
fixed it..

> 
I just found out how to get rid of "Couldn't resolve name for AF_INET6 Blah blah.com" in the most unobtrusive way:
Append the following line to /etc/mplayer/mplayer.conf (or ~/.mplayer/config for the current user only)
Quote:
prefer-ipv4 = yes
This doesn't disable IPv6 entirely, but just uses IPv4 as the default and falls back to IPv6 if the server is IPv6 only (or if the host cannot be found).
Reply With Quote


---

### Post by drpaul on 2007-02-25
running dapper, I get the same error message in a window, then it goes ahead and plays the stream.

I won't try to fix it when I get the sound out.

Paul

---

### Post by bwallum on 2007-03-08
I have been struggling to get BBC streams all day. Cracked it with this 

[https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9](https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9)

Hope it helps.

---


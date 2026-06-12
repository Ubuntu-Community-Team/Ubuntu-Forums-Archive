---
title: "Booting Help!"
date: 2013-01-21
forum: General Help
---

### Post by jazzmasterkc on 2013-01-21
Ok, I ran into some major issues...

I was trying to purge pulseaudio, and after I did sudo apt-get autoremove (following [these instructions]("http://ubuntuforums.org/showthread.php?t=1313253")) my computer froze in the middle of the command. After a while I had to kill power.

.. Now when I go to boot, Ubuntu freezes during loading screen where it shows "Ubuntu studio for creative humans". I ran recovery mode and noticed it starts the freeze at [stopped] Mount Network system files or something like that.

Any idea on how to fix this??

Edit:

I also have backtrack on dual boot, and now i get this when trying to open up my home folder:
/root/.selected_editor:1:1: not well-formed (invalid token)
/root/.pulse-cookie:1:0: not well-formed (invalid token)
/root/.profile:1:1: not well-formed (invalid token)
/root/.Xauthority:1:0: not well-formed (invalid token)
/root/.rnd:1:0: not well-formed (invalid token)
/root/.ICEauthority:1:0: not well-formed (invalid token)
/root/.armitage.prop:1:0: syntax error
/root/.bashrc:1:1: not well-formed (invalid token)
/root/.bash_history:1:0: syntax error
/root/.gtk-bookmarks:1:5: not well-formed (invalid token)
/root/.xsession-errors:1:0: syntax error

I know its not ubuntu, but this just started after today when I this whole disaster happened


Edit2:

I looked at my /etc/network/interface and didn't see eth0.. only
auto lo
iface lo inet loopback

Could this be the issue?

---


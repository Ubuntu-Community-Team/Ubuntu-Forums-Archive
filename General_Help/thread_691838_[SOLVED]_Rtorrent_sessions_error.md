---
title: "[SOLVED] Rtorrent sessions error"
date: 2008-02-09
forum: General Help
---

### Post by TidusBlade on 2008-02-09
When I try to start rtorrent, as root, it says;
```
rtorrent: Could not lock session directory: "./session/", held by "89-149-***-**.internetserviceteam.com:+8180".
```
I assume it has something to do with the TightVNC server that is currently running there? But in the TightVNC client, I'm not running any rtorrent clients on there so I don't think that would be it?
Any help will be appreciated :)
Thanks!
//EDIT: Tried to kill the VNC server, and still no luck.
///EDIT: Fixed itself or something so never mind :P

---

### Post by chochem on 2008-03-31
Uhm this may or may not be a completely different issue but I received the error message that my rtorrent session directory was locked by an instance running on my own machine (I was not trying to run as root, just as everyday user) When I concluded that this had to be a mistake as I could find no trace of rtorrent running anywhere, I entered the session directory and deleted the lock file. Problem solved.

---


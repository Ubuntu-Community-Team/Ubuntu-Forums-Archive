---
title: "rtorrent ~/.rtorrent.rc:2: Variable &quot;scgi_port&quot; does not exist."
date: 2007-11-25
forum: General Help
---

### Post by 3ntity on 2007-11-25
Hello,
I´m trying to get rtorrent + ntorrent working, however i have a problem getting rtorrent working. I followed the instructions [here,]("http://code.google.com/p/ntorrent/wiki/QuickStart"). I succeeded at compiling everything, and rtorrent works before following the last step: 
> Put this in your ~/.rtorrent.rc:
```
 # This will set rtorrent/scgi to listen on localhost, port 5000.
 scgi_port = 127.0.0.1:5000
```
After i do this i get the following error:
```
~$ rtorrent 
rtorrent: Error in option file: ~/.rtorrent.rc:2: Variable "scgi_port" does not exist.
```

I´ve tried this on 2 systems up to now and get the same error on both.

Thanks in advance for any help :)

---

### Post by konsole on 2007-11-25
have you configured your web server to talk scgi to rtorrent?

[http://libtorrent.rakshasa.no/wiki/RTorrentXMLRPCGuide](http://libtorrent.rakshasa.no/wiki/RTorrentXMLRPCGuide)

---

### Post by 3ntity on 2007-11-26
> **konsole said:**
> have you configured your web server to talk scgi to rtorrent?

[http://libtorrent.rakshasa.no/wiki/RTorrentXMLRPCGuide](http://libtorrent.rakshasa.no/wiki/RTorrentXMLRPCGuide)No i haven't... I'll give it a shot as soon i can

Thx :)

**Update:** Thanks, that worked :) Now just have to figure out how to stop all up&downloads at a a certain time but keep rtorrent running

---


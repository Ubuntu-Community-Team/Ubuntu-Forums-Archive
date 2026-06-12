---
title: "Problem with servers apps (cups, samba...)"
date: 2007-04-06
forum: General Help
---

### Post by Ago12 on 2007-04-06
Hello!

First, sorry for my english very crappy (but I try to improve it)

I have Feisty install, dist-upgraded a long time ago from Edgy, even if I think it is nor related.

I think I have smashed or badly edited an important file on my system a few weeks ago (at least I think, I can't remember what I did).

When I try to reach cups ( [http://localhost:631](http://localhost:631) ), I get a timeout.

When I restart samba, I have a weird message:
sudo /etc/init.d/samba restart
 * Stopping Samba daemons...                                                    start-stop-daemon: warning: failed to kill 5792: No such process
                                                                         [ OK ]
 * Starting Samba daemons...   


When I restart mpd:

 sudo /etc/init.d/mpd restart
Stopping Music Player Daemon: mpd.
Starting Music Player Daemon: unable to bind port 6600: Cannot assign requested address
maybe MPD is still running?
failed.


Of course, it isn't running.


I think I have blown a file about wich app listen wich port etc, but I don't know wich one it is, so I don't know how to regenerate it or wich package reinstall. I've tried to reistall cups, smb, mpd etc,  but no luck :(


Cups' error log is full of this kind of messages:
> E [06/Apr/2007:07:34:17 +0200] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
E [06/Apr/2007:08:15:46 +0200] Creating missing directory "/var/run/cups/certs"
E [06/Apr/2007:12:34:37 +0200] Creating missing directory "/var/run/cups/certs"
E [06/Apr/2007:15:38:00 +0200] Creating missing directory "/var/run/cups/certs"
E [06/Apr/2007:16:31:35 +0200] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.
E [06/Apr/2007:16:51:50 +0200] Creating missing directory "/var/run/cups/certs"
E [06/Apr/2007:17:17:56 +0200] Unable to bind socket for address 127.0.0.1:631 - Cannot assign requested address.


Please, could someone give me a hint? I really don't want to reinstall the system :(

Thanks anyway :D

---

### Post by Ago12 on 2007-04-09
Bump? :(

---

### Post by alexandrul on 2007-04-09
> 
sudo /etc/init.d/samba restart
* Stopping Samba daemons... start-stop-daemon: warning: failed to kill 5792: No such process
[ OK ]

it might mean that the pid 5792 is written in a file in /var/run/... (I think, can't verify this days), and samba can't delete the file (check the script to se exactly the file location), and with the cups error related to /var/run/... I think it is all about permissions accessing /var or /var/run

---

### Post by Ago12 on 2007-04-09
Hum, ok, I'm gonna look at that, thanks ;)

If anybody could be more specific, that would be great ;)

---

### Post by Ago12 on 2007-04-09
Hum, I've rmed /var/run/samba , no more error for this one! Thanks :D

I'm going to seek for the others...

---


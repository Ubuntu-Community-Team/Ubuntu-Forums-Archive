---
title: "LAN Messenger Wanted - Cross Platform without Internet"
date: 2013-04-24
forum: General Help
---

### Post by rbscairns on 2013-04-24
I have three computers; 2 x Win XP + 1 x Ubuntu 12.04 (Gnome) wirelessly connected through my router. What I am looking for is an application that will allow users on each computer to chat and transfer folders/files with each other.

The application needs to autoload at startup and notify when there is an incoming message/transfer. Ipmsg on the Win XP computers works well, however xipmsg (the Linux equivalent) is very "agricultural".

Any suggestions would be appreciated.

---

### Post by hkphooey on 2013-04-25
You might like to look at messengers using the Bonjour protocol. Pidgin will do that and is available for Windows and Ubuntu for example. There may be more

---

### Post by rbscairns on 2013-04-25
Thank you Hkphooey. I did not realise that Pidgin also worked in MS Windows. I will give it a try and report back.

---

### Post by hkphooey on 2013-04-27
Another thought occurs to me -- if you just want to transfer files, you could set up a Dropbox account shared between all computers, and it will sync the files between all computers. When it detects they're on the same LAN it will use the fast local connection to sync. There are notifications when a file is updated. 

Also ... bittorrent just released a sync client which does the same thing without the 'cloud' [http://labs.bittorrent.com/experiments/sync.html](http://labs.bittorrent.com/experiments/sync.html)

And finally, if you want a full project management / workgroup kind of thing, you might look at Collanos. [http://www.collanos.com/](http://www.collanos.com/)

---

### Post by rbscairns on 2013-04-28
File transfer was just part of what I wanted to do, however chatting was the main priority. This needed to be done even when my internet is down (not uncommon for me).

After installing Pidgin, GTK2 and Bonjour on my Win XP PC's, all works well. I have LAN messaging between Windows and Linux PC's without going through the internet.

---


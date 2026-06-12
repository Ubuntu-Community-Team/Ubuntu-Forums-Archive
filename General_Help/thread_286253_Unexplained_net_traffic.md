---
title: "Unexplained net traffic"
date: 2006-10-27
forum: General Help
---

### Post by jamespi on 2006-10-27
Usually my ubuntu box is reasurringly free of internet traffic when i'm not doing anything over the internet, but i've just noticed that about .5kb/s up and down are being displayed on the system moniter and i'm not doing anything over the net. the only inbound ports i have open on firestarter are 6881-6889 for bittorrent. i was running azureus until about an hour ago, but it was not doing anything for about 2 days anyway.

is there any way to tell what programs are using this bandwidth? is it the automatic update system? how can i tell?

---

### Post by skymt on 2006-10-27
Usually you get some extra traffic for a while after using Bittorrent, because some clients in the swarm will keep asking you for parts of the file.

---

### Post by Swab on 2006-10-27
open a terminal and type: netstat -a

---

### Post by ~LoKe on 2006-10-27
I believe the network manager will send/receive signals to make sure it's still online?  If it's just a fraction of a kB, I wouldn't give it a second thought.

---

### Post by jamespi on 2006-10-29
yeah its just usually i have nothing at all. and i was seeing a sustained .5k up and down for more than an hour. i have loads of stuff downlaoding at the moment but i''ll do netstat -a when its idle again

---


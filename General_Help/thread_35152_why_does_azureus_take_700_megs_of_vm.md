---
title: "why does azureus take 700 megs of vm?"
date: 2005-05-17
forum: General Help
---

### Post by atf487 on 2005-05-17
I have this problem with azureus, after a few minutes of downloading, the app starts taking tons of memory. i don't know why, and it makes the computer totally unusable. 

it doesnt happen with limewire, the other java app i have. so anyone know why it would be happening?

---

### Post by nad on 2005-05-17
azureus allocates the total amount of disk space required for the download upon setting up the torrent.

---

### Post by JonahRowley on 2005-05-17
Azuerus is written in Java, which is just a memory hog.  Every non-trivial Java program I've used has used obscene amounts of RAM, it just goes with the territory of using an application written in Java.  I don't bother with Java applications anymore, I'm not upgrading just to use a bittorrent client..

---

### Post by zab on 2005-05-17
[QUOTE=atf487]it doesnt happen with limewire, the other java app i have. so anyone know why it would be happening?[/QUOTE]

cause we're better coders?  :grin:

---

### Post by Dax0r on 2005-05-18
u Can use the 2.2 version,is better than 2.3

---

### Post by atf487 on 2005-05-18
[QUOTE=nad]azureus allocates the total amount of disk space required for the download upon setting up the torrent.[/QUOTE]

yeah, but wouldnt it allocate the space on the drive instead of on the swap partition?

anyway, i've downloaded bittornado which isnt bad, and i may roll back to 2.2.0.2

thanks.

---

### Post by alphazero on 2005-05-18
If I'm not mistaken, Azureus 2.3 takes up more memory because of it's new DHT feature. What it does is in essence create a trackerless network (as long as you get the torrent) since the clients themselves act as a tracker-cluster. There should be some toggles to turn it off. That might ease the load.

---

### Post by bored2k on 2005-05-18
[QUOTE=alphazero]If I'm not mistaken, Azureus 2.3 takes up more memory because of it's new DHT feature. What it does is in essence create a trackerless network (as long as you get the torrent) since the clients themselves act as a tracker-cluster. There should be some toggles to turn it off. That might ease the load.[/QUOTE]
 Without that feature, there's really no reason to use Azureus :\

---


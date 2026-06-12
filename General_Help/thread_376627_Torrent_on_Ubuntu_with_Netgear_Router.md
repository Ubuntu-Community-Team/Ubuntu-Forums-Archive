---
title: "Torrent on Ubuntu with Netgear Router"
date: 2007-03-05
forum: General Help
---

### Post by stueyboy on 2007-03-05
I am hoping that I can get some assistance with this annoying problem as I can't quite find the answer on here in any previous posts.

I am using a Netgear DG632 ADSL router modem to connect to the internet and when I am using a bit torrent client on my Ubuntu system it will work for a random period of time then the internet connection will get dropped.

Now, I have tried about four different torrent programmes (ktorrent and azureus being my most favoured) and they all do the same thing. Reading around other places, I thought I had it sorted by limiting the number of connection the bit torrent client was allowed to make. This works partially as the connection stays up for a bit longer (maybe 2-3 hours) before dropping.

This situation isn't replicated on my XP laptop with azureus downloading torrents. It isn't torrent specific either. I do think it is something to do with the number of connections being opened on Ubuntu but I just don't know exactly what it is. I currently have azureus limited to 31 connections.

The strange thing is, that I previously had torrent working fine before I rebuilt the system but it is almost impossible to tell what has changed. The only relevant thing I had trouble with on this install was getting the network card to connect to the internet. I solved this by specifying all the info manually and adding the DNS addresses.

Anyway, if anyone has any ideas, I'd be grateful. It's not critical but is one of those irritating little things which keeps bugging me about an otherwise fantastic OS.

Ta


Stu

---

### Post by chewearn on 2007-03-05
Here is the Azureus wiki page, listing your Netgear router as one of the bad routers:
[http://www.azureuswiki.com/index.php/Bad_routers](http://www.azureuswiki.com/index.php/Bad_routers)

Probably, you have already tried the things suggested in this page.  Except the last item: "Getting a new router if all else fails".  :(

Sorry for the negative post.  I am in the same boat (owned another of bad router, but I managed to keep it alive by limiting number of connections to 200).

---

### Post by Arup on 2007-03-05
I have the same router and use Deluge with no problems, the problem maybe that you have logging enabled for inbound connection rules, turn that off as it will fill the router memory up very quicly leading to connections being dropped. The Netgear router after the latest firmware upgrade has no problems handling torrents or high number of connections.

---

### Post by stueyboy on 2007-03-05
> **Arup said:**
> the problem maybe that you have logging enabled for inbound connection rules


Thanks for the replies. The logging thing might just be what the problem is as when you set up a firewall rule it checks that by default, so I might try unchecking that and see if it makes any difference. I mentioned that my XP based azureus experiences are not as bad as with Ubuntu but it will still lock up but after a longer period. I have tried Deluge and it did the same thing. I also patched the firmware on the router to get round the file sharing issue. I'd rather not buy a new one as it is quite a goo dproduct, much better for instance than the BT home hub which lasted about a month on my network (piece of crap)

Thanks
Stu

---

### Post by stueyboy on 2007-03-06
Quick update on the azureus, netgear situation;

I did as suggested and disabled logging for the firewall rules on my netgear router then left the PC on all night with a large queue of torrents to deal with and this morning, they had all downloaded and some had seeded and in addition, the internet connection was still active, so this seems to have sorted out the problems for me at least. Thanks for the replies folks and maybe this might help some other folks with similar problems.

Stu

---

### Post by vanth13 on 2007-08-10
I have the same probem... would you please explain me how to disable logging for the firewall rules? I don't knok what it means...

---

### Post by stueyboy on 2007-08-12
Sorry I haven't been keeping up with the posts on here. Basically, I now use kTorrent for my downloading as it seems less hungry on ths system and mnore reliable. Also, you can use an IP filter set to stop any pesky snooping on the downloading.

The main thing which stopped the router from hanging was to switch off the logging function when opening the firewall ports on the router. I guess it gets to a stage where the routers internal memory is full and just plain gives up.

---


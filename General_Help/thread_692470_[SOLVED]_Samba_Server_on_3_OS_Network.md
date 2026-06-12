---
title: "[SOLVED] Samba Server on 3 OS Network"
date: 2008-02-09
forum: General Help
---

### Post by pmshirey on 2008-02-09
I have Vista, XP 2nd edition, and Ubuntu crammed all in the same house(literally). I would like to make a Samba Server. I need to know the best way to do this without hosing my computers.

---

### Post by coastdweller on 2008-02-09
> **pmshirey said:**
> I have Vista, XP 2nd edition, and Ubuntu crammed all in the same house(literally). I would like to make a Samba Server. I need to know the best way to do this without hosing my computers.

If you have individual machines then state what you want to share/connect to and how.

Here on the network here I have my ubuntu servers connecting to each other via NFS.
My head-end server (webserver, jinzora and torrentflux-br4t) runs samba so the windows machine can connect to the linux shares.

The reason I use NFS is so that BMF (Bad Mutha *****r) is the file server for the other linux servers) Torrents, music, movies all come from BMF to the head-end via NFS).

BMF runs samba so that the windows machines can get to the files created by the linux torrent server.

So what ya want to do?

:guitar:

---

### Post by pmshirey on 2008-02-09
my system won't let me access the server computer :( im installing windows on it tommorow :(:(:mad:

---

### Post by jetsam on 2008-02-09
People generally have good luck with [this]("http://www.europe.eclipse.co.uk/Ubuntu/Ubuntu-on-win-network.htm") guide (simpler), or with Stormbringer's how-to [here]("http://ubuntuforums.org/showthread.php?t=202605").

---

### Post by pmshirey on 2008-02-09
Thanks for the instructions. I did steps 1,2,and 4, but that was it.

---


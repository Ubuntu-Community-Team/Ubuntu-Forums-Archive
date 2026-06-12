---
title: "Ubuntu Server 12.04 Transmission Torrent"
date: 2014-04-23
forum: General Help
---

### Post by adam17 on 2014-04-23
Hi,

Does anyone know how I can use the terminal to add or start a new torrent file downloading on my home server.

I can access the server from anywhere but unfortunately the web interface does not work from my work address is there a way of controlling transmission using the terminal.

eg.

transmission - /goto/thisfile.torrent add or start

Thanks

---

### Post by ericpatch on 2014-04-23
[http://manpages.ubuntu.com/manpages/intrepid/man1/transmission-remote.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/transmission-remote.1.html)

This should do it:

transmission-remote -a /path_to/mytorrent.torrent

---

### Post by CaptainMark on 2014-04-23
Based on the fact you say you can access the server anywhere I'm going to assume (hopefully) you have setup an SSH server, if so you should be able to access the transmission web ui easily using port forwarding running ```
ssh -L XXXX:HOST:9091
```Assuming you have the transmission web ui running on the standard port 9091 you'll then just have to point your browser at work to localhost:XXXX (XXXX can be any port above something like 1024?? so long as you use the same port as in the ssh command)

---


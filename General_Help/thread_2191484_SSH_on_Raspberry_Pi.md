---
title: "SSH on Raspberry Pi"
date: 2013-12-02
forum: General Help
---

### Post by ranger1021994 on 2013-12-02
I have a Raspberry Pi which I have connected over LAN.
I wanted to configure it as a torrent downloader.

I downloaded qbittorrent-nox and started it over SSH
I ran
```
qbittorrent-nox&
```
The proccess started and so did the WebUI
I added the torrents and it started downloading.

Now the problem is, as soon as I close my SSH connection, the WebUI stops working.
Can anyone suggest a way to make sure that the torrent client runs even after I close my SSH connection ?

---

### Post by pbrane on 2013-12-03
You could try this:
[http://askubuntu.com/questions/8653/how-to-keep-processes-running-after-ending-ssh-session]("http://askubuntu.com/questions/8653/how-to-keep-processes-running-after-ending-ssh-session")

---


---
title: "Transmission: External HDD error: Permission denied"
date: 2016-09-04
forum: General Help
---

### Post by markodd on 2016-09-04
Hello,

I'm running transmission-daemon on my raspberry pi via ssh, which is running Ubuntu-Mate 16.04.1 but I'm having some permissions issues. I've an external HDD connected to my PI, and, after following [this]("https://www.youtube.com/watch?v=flhGmgbAqZA") tutorial I get the permissions denied error: "Unable to save resume file: Permission denied".

The commands of the linked tutorial are the following (pi is my username):

I mounted the HDD on /mnt (after decrypting as my HDD is LUKS encrypted)

```
sudo chown pi:pi /mnt/pi/myhdd/torrents

sudo vim /var/lib/transmission-daemon/.config/transmission-daemon/settings.json (Changed password, and path to my torrent folders)

sudo vim /etc/init.d/transmission-daemon (Changed "USER:debian-transmission" to "USER:pi")
```


I also did the top answer of [this]("https://raspberrypi.stackexchange.com/questions/4378/transmission-permission-denied-on-usb-disk") link but it didn't help.


Doing "ls -l" gives me the following:

```
 drwsr-xr-x  4 pi pi  4096 Set  3 16:16 torrents
```

EDIT:

I've now also edited /lib/systemd/system/transmission-daemon.service and made it: "USER:pi"

---


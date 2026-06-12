---
title: "Bittorrent in console?"
date: 2005-06-11
forum: General Help
---

### Post by Phixion on 2005-06-11
Hello there, I would like to use Bittorrent for .torrent files but I can't seem to get it working. Its confusing me as I've had it working before.

Anyway heres the syntax I'm using to try and make it work, where am I going wrong?

./btdownloadcurses.py /home/mark/1.torrent --minport 49152 --maxport 65535 --max_upload_rate 14 --saveas /mnt/d/Downloads/Games/<torrentdir>

Cheers.

---

### Post by jgoguen on 2005-06-11
Try just using btdownloadcurses.  Make sure it's in your path by using the command 
```
which btdownloadcurses
``` 
and then if it is, likely it's in /usr/bin, just type 
```
btdownloadcurses /home/mark/1.torrent --minport 49152 --maxport 65535 --max_upload_rate 14 --saveas /mnt/d/Downloads/Games/<torrentdir>
```
If it's not in your path, make sure you have it installed 
```
apt-cache --installed search bittorrent
```
and if so maybe you need to update your path.  If not, then 
```
sudo apt-get install bittorrent
```
will set you right up.

---

### Post by Phixion on 2005-06-11
Thanks a bunch, that works fine, cheers m8 :)

---


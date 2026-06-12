---
title: "Help me replace Windows"
date: 2008-04-04
forum: General Help
---

### Post by general.chaos on 2008-04-04
Hi all, I had ubuntu running well on my main PC, but since then I had put Windows back on because I am using it as an HTPC now, and my video card looked horrid on my HDTV under Ubuntu.

Now I have a new desktop machine I would like to move over to Ubuntu, but only if it can completly replace what it is doing now under windows.

I need it to be able to:

Run Ampache or something similar
Run an FTP server
Remote Desktop both ways
I'd like a WebUI for a torrent app (not that vital, but nice)
Must be able to read/write SMB shares from my Vista machine, and vice versa

Do you think its possible?

Thanx

---

### Post by Bablefish on 2008-04-04
I am telling you that you can not completely dump Windows. Too much runs on it, and frankly there aren't a lot of programs that can totally replace them. I fully admit I have been using Ubuntu for more than a year. But I can't run my main scanner on it. Xsane doesn't give me the control my Windows program has. It's either full page scan or nothing. I admit Ubuntu is great for a lot of things, but a total replacement I very much doubt it.

---

### Post by general.chaos on 2008-04-04
as long as Ubuntu can do all the things mentioned above I would gladly switch again.

---

### Post by Twitch6000 on 2008-04-04
Lets see here everything you mentioned I see Ubuntu Linux doing one way or another.
You might have to download a few things but,yeah you can do it.I know remote desktop comes on by default.Torrents are in add/remove.That other stuff are aswell or are on google.So yeah I am sure you can do the switch.

---

### Post by cdenley on 2008-04-04
-Run Ampache or something similar
ampache is in the ubuntu repository

-Run an FTP server
proftpd,vsftpd
gproftpd for a gui frontend

-Remote Desktop both ways
vnc runs on windows and linux

-WebUI for a torrent app
azureus, torrentflux, clutch

-Must be able to read/write SMB shares from my Vista machine, and vice versa
samba

> I am telling you that you can not completely dump Windows. Too much runs on it, and frankly there aren't a lot of programs that can totally replace them.
I completely dumped windows. The only time I use it is for testing at work. Everything I need is in the ubuntu repository.

---

### Post by general.chaos on 2008-04-14
Well, I got nearly everything working.

Remote desktop via VNCViewer for windows works great,
Deluge with WebUI is fan-friggin-tastic
Apache install was a little pain with securing your php and sql etc, but its up, secure, and works great!

My last issue however is SMB shares.

My vista machine can access my Ubuntu machine, but I can't get Ubuntu to recognize my Vista shares.

I've followed every tutorial I could find and none of them have worked for me :(

Any Advice?

---

### Post by Martje_001 on 2008-04-14
Do you want to mount your SAMBA drives? What's the IP of the computer you're connection to? What have you tried 'till now?

---

### Post by general.chaos on 2008-04-14
well, I installed all the samba fs packages, and the CIFS ones.

I followed this guide along with many others, nothing worked:

[http://ubuntuforums.org/showthread.php?t=373917](http://ubuntuforums.org/showthread.php?t=373917)

---

### Post by Martje_001 on 2008-04-14
Run this command to mount your vista shares:

```
sudo mount -t smbfs -o username=$windowsusername,password=$password $windowsshare $mountdir
```
**$windowsusername:** Username of Windows you wish to login with
**$password:** says it all..
**$windowsshare:** Directory of the windows share
**$mountdir:** For example /home/yourusername/samba

What's the problem if you run that command? (what's the output?)

---

### Post by Martje_001 on 2008-04-14
Almost forgot to say: If the command does not returns any errors and you're still not able to read/write to the mount-directory do this:
```
sudo chown yourusername:yourusername /home/yourusername/samba
sudo chmod 777 /home/yourusername/samba
```

---

### Post by general.chaos on 2008-04-14
Ill test this when I get home, but it seems like the same thing i've already tried.   I'll post back and let you know.

Thanks.

---


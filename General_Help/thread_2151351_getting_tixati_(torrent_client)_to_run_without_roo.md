---
title: "getting tixati (torrent client) to run without root"
date: 2013-06-04
forum: General Help
---

### Post by Toitovna on 2013-06-04
Hi, I'm running Lubuntu 12.10 Quantal.

I've downloaded and installed the Tixati torrent client, however when I open it simply by clicking, it tells me that my download folder /mnt/teradrive/Downloads could not be found. I discovered that if I ran the client as root it had no such troubles finding the folder, however I know that it is not best practice for me to run everyday applications as root. How would I modify the permissions so that the program is allowed to read and write to this directory?

Also, I've edited the /etc/rc.local file to run "/usr/bin/tixati %F" on startup - however I believe that rc.local runs commands as root, so what would I need to do once I fix this to make sure the program is just run normally at startup?

Thanks.

---

### Post by arubislander on 2013-06-04
Hi.

It seems you want your torrent files to download to the Downloads directory of a drive you've mounted in /mnt? How is this drive being mounted? Can you verify that when you startup your computer the drive is actually mounted in /mnt/teradrive? If it isn't you're not writing your files where you think you are.

If it is acceptable for Tixati to run after you've logged on you could look at this thread: [http://ubuntuforums.org/showthread.php?t=1518818]("http://ubuntuforums.org/showthread.php?t=1518818")

---

### Post by Toitovna on 2013-06-04
Hey arubislander, yes teradrive is one of three HDDs I have mounted in /mnt and that's done in the fstab file. The folder is definitely there, I can see it + all my other mounted folders with my file manager, plus tixati can find it when I run as root, it's weird...

I should also mention that before I used this client, I was using qBitTorrent, which downloaded to that same folder without any difficulties (when run as normal user).

but thanks for that link, I wasn't aware of that method :)

---

### Post by arubislander on 2013-06-04
Hi Toitovna,

In that case, check the permissions on the the /mnt/teradrive/Downloads folder. Is the drive formatted as ext3/4 or as FAT32/NTFS? if the former you can change the permissions with
```
$ sudo chown -R [your-username].[your-usergroup] /mnt/teradrive/Downloads
```

And all shoud be well after that.

---

### Post by Toitovna on 2013-06-04
sorry should have mentioned that the drive is ntfs .. will I need to add in some other variable to chown to make it work?

---

### Post by Toitovna on 2013-06-04
ok so I did my own googling and I've now edited the fstab file with my uid and gid so that I'm allowed to access the whole /mnt/teradrive folder, and put a link to the application into ~/.config/autostart. Everything is now working as it should! (marked as solved)

thanks,

toitovna

---


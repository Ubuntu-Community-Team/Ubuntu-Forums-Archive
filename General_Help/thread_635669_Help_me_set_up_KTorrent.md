---
title: "Help me set up KTorrent"
date: 2007-12-09
forum: General Help
---

### Post by Sicundercover on 2007-12-09
This is where im at. I have everything configured but I cant get to my other hard drives.

KTorrent just doesnt see them at all. I get this as an error when I try to manualy type the drive path in and import a torrent.

```
Cannot copy /media/Big Bob/Import 
Destination/UTorrent/Kane_and_Lynch_Dead_Men-HATRED.torrent to media:/sdc1/Import 
Destination/UTorrent/tor0/torrent: Could not write to /media/Big Bob/Import 
Destination/UTorrent/tor0/torrent.part.
```

So from here I checked my properties on my drives and they are set to add and delete but the owner is root. So I logged in as root (I know this is frowned upon) and tried to change owner but it wouldnt allow me to change the owner (I have no clue if you can even do this I was just trying). I also made sure that it was set to read write and it was. I then logged back out and logged in as user.

Im out of Ideas.

Anyone got any?

---

### Post by barney_1 on 2007-12-09
You should be able to change the ownership with:

```
sudo chown USER:USER /media/Big\ Bob
sudo chown -R USER:USER /media/Big\ Bob/*
```

you need to replace USER with your login name.

Give that a try and post any errors you get from it.

---

### Post by maybeway36 on 2007-12-09
Make sure you are in the group plugdev, and if you are and that doesn't help, post your /etc/fstab (which defines permissions for FAT and NTFS drives.)

---

### Post by Sicundercover on 2007-12-09
Thanks guys I ended up getting ntfs-3g to make it work for me.

---


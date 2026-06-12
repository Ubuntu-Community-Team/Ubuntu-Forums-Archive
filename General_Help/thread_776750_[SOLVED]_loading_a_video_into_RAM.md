---
title: "[SOLVED] loading a video into RAM"
date: 2008-04-30
forum: General Help
---

### Post by tamoneya on 2008-04-30
So today I had a train ride that I had to take and I was planning on watching videos on my laptop.  Typically I move the video onto a flash drive and play it off of that since it does not require my harddrive to spin and saves some battery life.  Today however I forgot my flashdrive and I had to run it of my harddrive which was not ideal.  This got me thinking though.  Could I possibly load my video onto my RAM.  I typically am using about 800MB out of my 2GB so there is definately the space to put my 700 MB video in but the question is how.  
I came up with two ideas but am uncertain how to implement them.  1) Change the read ahead on vlc so that it just reads the entire file at the start into RAM.  Not sure how well VLC will handle this since it probably isnt designed to be used that way.  2) "partition" part of my RAM and mount it so that I can place my video into the RAM "partition" and then play this file from vlc. 
I do not know how to implement either of these ideas and I am curious to know what you guys think about the pros and cons of each.  I think this would actually be more energy efficient than a flash drive but I am not positive.

---

### Post by ryanhaigh on 2008-05-01
I dont' know if this would work but it is simpler than creating a ramdisk (thats what the second option you presented it you can google for more info on that). 

Basically what you want to do is read the entire file into the systems cache, to do this is quite simple.
```

cat /path/to/file > /dev/null

```
This should load the entire file into memory, using /dev/null means its not printed to screeen so that the operation is faster. However the drive MAY still spin up to set the atime for the file (access time) you can avoid this by adding noatime to the options for the drive in /etc/fstab.

---

### Post by jocko on 2008-05-01
I may have found something you could try:
```
sudo mkdir /media/tmpfs
sudo mount -t tmpfs tmpfs /media/tmpfs -o size=1G,noatime
```
If I understand this correctly it does exactly what you want (if you don't want it to show up as a drive on your desktop, just put the mountpoint somewhere else).

---

### Post by tamoneya on 2008-05-01
Thanks guys.  This is exactly what I was looking for.  I will give this a try on sunday when I have another trip to make.

---


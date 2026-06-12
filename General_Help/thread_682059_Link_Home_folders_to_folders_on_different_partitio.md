---
title: "Link Home folders to folders on different partition"
date: 2008-01-29
forum: General Help
---

### Post by gregcss on 2008-01-29
i want to link the folders in Home (Music, Data, Pics, Video) to folders on different partition also called (Music, Data, Pics, Video). Using 'Make Link' doesnt do what i want it to. I dont like having /home on different partition because when i reimage the partition the /home will still be the same with possible errors ) 

Any ideas?

---

### Post by cmnorton on 2008-01-29
It seems like you want to take folders on one partition and move them to same named folders on another partition. I am assuming you want to do that.

Assuming the partition is already mounted, whether on a separate disk or not, then

1) Back up everything that would be affected somewhere other than where you are going to move these folders.

2) Make sure nothing in the folders is in use (opened by some program).

3) Create the new directories (in the new location)

4) Move (mv) the directories/files to the new location

5) Create one or more links (ln -s) to the new location from the old location. This is deliberately vague, because it would be helpful to know what you want to move (if you indeed want to move your files). You might only need to move one high level directory and create one link.

---

### Post by gregcss on 2008-01-29
i dont want to move anything, just move the target. For example in Windows if you right click on my documents you can set the target to any folder you want. I would like to do the same for the home folder.

---

### Post by heindsight on 2008-01-29
First remove the directories from your home directory, then create the links.
For example, I have a partition mounted on /home/heindsight/media with all my music in
/home/heindsight/media/Music,  my videos in /home/heindsight/media/Videos and my pictures
in /home/heindsight/media/Picures, so I did:

```
cd /home/heindsight
rmdir Pictures Music Videos
for d in media/{Pictures,Music,Videos}; do ln -s $d; done
```

---

### Post by gregcss on 2008-01-30
thanks, i will try this when i get to be Ubuntu PC. not sure if it matters but my 2nd partition is on /media/sda3

---

### Post by gregcss on 2008-01-30
That worked. Thanks so much

---


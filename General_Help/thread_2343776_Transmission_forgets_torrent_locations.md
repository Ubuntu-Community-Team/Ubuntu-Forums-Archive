---
title: "Transmission forgets torrent locations"
date: 2016-11-19
forum: General Help
---

### Post by noobuntu3 on 2016-11-19
I'm pretty new to Linux but I love it so far. I do run into an awful lot of things I don't understand how to do (mainly involving Terminal), but with enough support from more experienced users I've been alright.

So here's my problem: I downloaded a bunch of torrents via Transmission onto my small SSD. I then installed a HDD which is NTFS format and has Windows 7 on it. Then within Transmission I used **Set Location -> Move from the ****current folder** to move the torrents to the HDD. Now every time I restart the computer I have to set the location of all my torrents and then tell them all to start in order for them to seed. I even tried moving them back to the original location on the SSD and that didn't work (although I can't remember if I had figured out yet that you have to tell them all to start in order for the error message to go away). I am running Ubuntu 16.04.

---

### Post by #&amp;thj^% on 2016-11-19
Sorry I have no solution for you...but just my experience in helping friends. (And the fact I just don't use Windows)
NTFS is a windows F/S system (I know you are already aware of this), so in my experience there is no right or good way to do that.. you should use a native F/S for linux like ext3/4 or even use exfat (or known as Fat 32 also) would be better.. userspace drivers (fuse + ntfs-3g) is more CPU hungry and IO hungry.

I just don't think torrent downloads and NTFS on linux is a good match.
Write performance is poor with NTFS drives. 
Kind Regards

---


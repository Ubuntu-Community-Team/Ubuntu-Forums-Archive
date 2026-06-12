---
title: "Problems with video"
date: 2008-02-23
forum: General Help
---

### Post by L815 on 2008-02-23
I reinstalled the Gusty today and am loving it :) 

I used automatix2 to install all the codecs and other things I wanted to make things easier.

Sound works fine, but I'm having trouble playing avi files (not sure about other video types).

When I try and play a video file in ANY media player, it opens, then automatically closes again by itself. I don't see any errors or any video at all. The program just opens and closes. 


I was wondering if anyone knew what was going on? This is the only real problem I'm having so far, and I am pretty sure automatix2 installed all the codecs which include avi (i think).


Thanks in adv.

---

### Post by taurus on 2008-02-23
Which media player did you use to play your avi?

And for the record, you don't need automatix2 to install codecs in Gutsy.

---

### Post by L815 on 2008-02-23
I tried VLC, MPlayer, and Totem. 

Does it matter if I used automatix? or should I uninstall it and reinstall the codecs manually?

---

### Post by taurus on 2008-02-23
Since it's your machine, I will let you decide whether you should remove automatix or not.  And if you need codecs for Ubuntu, here is a guide.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by L815 on 2008-02-23
I understand the reasoning behind the codecs on linux, but would it fix my problem if I do it manually instead of automated?

---

### Post by taurus on 2008-02-23
Try running those media players from a terminal to see what is the problem.  Assuming you are in the same directory where the movie, movie.avi, is, try

```
vlc movie.avi
-or-
gmplayer movie.avi
```

---

### Post by L815 on 2008-02-23
Output:
```

VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87
l815@l815-laptop:/media/sda2/Users/L815/Documents/Torrents/A.L.Interieur.FRENCH.

```

Does it matter if the video uses subtitles (.srt).

It's located on an ntfs partiton (my windows part.) but I get the same when I copy it over to the linux partition.


EDIT:

I tried it with gxine just now, it loads the video, plays it and displays the subtitles, but the video is black :/

---

### Post by L815 on 2008-02-24
Okay I found the solution. It had to do with having desktop effects enabled.

This is the thread that helped me fix it:
[http://ubuntuforums.org/showthread.php?t=480357](http://ubuntuforums.org/showthread.php?t=480357)

---


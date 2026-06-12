---
title: "video play problem"
date: 2008-05-31
forum: General Help
---

### Post by kalgil on 2008-05-31
hey i got a problem with my players,i am unable to see the video in my video players,i can only hear audio,   the players i use are vlc,movieplayer,

---

### Post by latna on 2008-05-31
Play a movie from a terminal and paste the ouput in between quote tags. That will give us some idea of what might be happening.

```
vlc name_of_movie_file
```

---

### Post by kalgil on 2008-06-01
iam unable to play my video files using my video players,only the audio is being played when i try to play my video ...
 when i tried to play video using my terminal 
     the movie is being played with no video and the message is displayed as shown below


"VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 0 (root)
***************************************
* Running VLC as root is discouraged. *
***************************************

 It is potentially dangerous, and might not even work properly.
[00000281] main playlist: stopping playback"

---

### Post by bingoUV on 2008-06-01
Instead of running vlc, could you give the output of the following 2 commands from the terminal
```

echo $USER
whoami

```

---

### Post by kalgil on 2008-06-01
i logged as super user and the output of the above commands is this


root@sriram-desktop:/home/sriram# echo $user

root@sriram-desktop:/home/sriram# whoami
root

---

### Post by kureyamu on 2008-06-01
hi

if it's a codec problem, then you may have to update yr codecs

i am not on ubuntu at this very moment but using Linux Mint ... as far i remember, if you go to System/Administration/Synaptic Packet Manager, you can search for and install Ubuntu - restricted ... (its name is similar to that) which is a collection of proprietary media codecs ... install those and reboot and see if it solves the problem

regards

kureyamu

---

### Post by latna on 2008-06-01
The answer then is to not log in as root. I'll spare you the lecture on why it's so dangerous. ;) There are plenty of discussions in the forum on that subject.

---

### Post by bingoUV on 2008-06-01
You know the answer, don't log in as root.

If you insist, you must have created a non-root user during Ubuntu install, say sriram. Just run 
```

sudo -u sriram vlc <file_name>

```

EDIT : BTW, that was $USER, in upper case / capital letters. It did not matter much here, but in general linux commands and filenames do not work correctly if in the wrong case.

---


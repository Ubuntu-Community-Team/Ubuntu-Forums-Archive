---
title: "Request for video recording help"
date: 2020-09-07
forum: General Help
---

### Post by Old Jimma on 2020-09-07
Hi Forum People,

At age 104 I've been asked to make four brief (approx 20 seconds) videos of myself saying a few lines out of newspaper.

THen, they want me to glue those 4 videos together ... one after the other ... to make a single video... in a commonly use video format.

I want to use my old laptop that has built in web cam and speaker.

How can I do this. I don't have any idea!

Help!

Thanks!
Old JImma form the Old Country

---

### Post by HermanAB on 2020-09-08
I always go back to *kdenlive *for video editing.  No video editors are easy to use, but some are much worse than others.

How to record the clips in the first place - there are various options - even Zoom can be used to record a clip.

---

### Post by dragonfly41 on 2020-09-08
Some more tips here ..
[https://forums.linuxmint.com/viewtopic.php?t=232922](https://forums.linuxmint.com/viewtopic.php?t=232922)

For basic tips read .. post#10
[https://forums.linuxmint.com/viewtopic.php?p=1235945&sid=1c98f8c620a817bd9f7937d9d1b26b8b#p1235945](https://forums.linuxmint.com/viewtopic.php?p=1235945&sid=1c98f8c620a817bd9f7937d9d1b26b8b#p1235945)

---

### Post by ajgreeny on 2020-09-08
For simplicity I suggest **guvcview** to record and save your clips but the joining is more difficult.

Kdenlive  will do though I prefer Openshot, and ffmpeg can also do it using command line, though you may prefer a GUI.

---

### Post by SeijiSensei on 2020-09-08
Cheese can record videos: [https://help.gnome.org/users/cheese/stable/video-record.html.en](https://help.gnome.org/users/cheese/stable/video-record.html.en)

I picked up KDEnlive when I had to caption a recorded session from Zoom. Took an hour or two to sort it all out, though I think if you're just concatenating video clips, it should be pretty easy.

ffmpeg can also do this from the command prompt with its concatenate command: [https://trac.ffmpeg.org/wiki/Concatenate](https://trac.ffmpeg.org/wiki/Concatenate) That page has some complicated solutions, but the simplest method is to put the filenames in a text file as the first example demonstrates. The example uses .wav files, but it should work fine with videos in a standard container format like .mp4, .mkv, or .webm. Cheese now creates its files using .webm.

---

### Post by T6&amp;sfpER35% on 2020-09-08
i once used **Openshot** to join some vids together ,wasn't too difficult. Just need to play around a bit with it.

---

### Post by HermanAB on 2020-09-08
BTW, you could simply concatenate the clips with *cat*.  The player may have a hiccup at the joint, or it may not.  It very much depends on the error handling of the player.  

Most of them will carry on playing smoothly:

$ cat file1.mp4 > filenew.mp4
$ cat file2.mp4 >> filenew.mp4
$ cat file3.mp4 >> filenew.mp4

One > means make a new file.
Two >> means append to the end of the file.

---

### Post by ajgreeny on 2020-09-10
> **HermanAB said:**
> BTW, you could simply concatenate the clips with *cat*.  The player may have a hiccup at the joint, or it may not.  It very much depends on the error handling of the player.  

Most of them will carry on playing smoothly:

$ cat file1.mp4 > filenew.mp4
$ cat file2.mp4 >> filenew.mp4
$ cat file3.mp4 >> filenew.mp4

One > means make a new file.
Two >> means append to the end of the file.
I tried this Herman but could not get the output files to play using anything.

It certainly managed to create a new file of just about the size I would expect, ie adding the two sizes together, but VLC, mplayer, parole, all of those showed no output at all when I tried to play the joined files.

---


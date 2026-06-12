---
title: "Streaming Videos"
date: 2007-04-22
forum: General Help
---

### Post by CheeseQueen452 on 2007-04-22
When I play streaming videos, they tend to be a little choppy. Sometimes, they even skip like a record(remember those?). I assume that I need a faster processor, unless there was something else I could do. I currently have a 1ghz processor, which I thought was sufficient. However, my motherboard can't handle a faster processor & I don't have another one available to me right now. Any words of wisdom on this?

Here are 2 clips I made with my camera to show what I'm seeing.....
This one is choppy, & it skips at the end of the clip:
[http://smg.photobucket.com/albums/v209/Sasafrass/MyPix/?action=view&current=MVI_1785.flv](http://smg.photobucket.com/albums/v209/Sasafrass/MyPix/?action=view&current=MVI_1785.flv)

This one is also choppy, & it pauses 3 times:
[http://smg.photobucket.com/albums/v209/Sasafrass/MyPix/?action=view&current=MVI_1768.flv](http://smg.photobucket.com/albums/v209/Sasafrass/MyPix/?action=view&current=MVI_1768.flv)

---

### Post by CheeseQueen452 on 2007-04-24
Anyone?

---

### Post by itsjustarumour on 2007-04-24
Hi,
Which app are you using to view the video streams with?

---

### Post by Rhubarb on 2007-04-24
Well, sometimes I find it's just best to download the video, rather than trying to stream it in.
It could be choppy because of your processor, your internet connection speed, or the media player you choose to play the content.

So, if you want to download your videos, in a console, just type in:
```
wget http://smg.photobucket.com/albums/v2...t=MVI_1785.flv
```

If you want to download a video that uses mms:// (or sometimes an .asx playlist):
```
sudo aptitude install mimms
mimms mms://insert_the_name_of_the_url_here
```

If you want to download something from youtube:
```
sudo aptitude install youtube-dl
youtube-dl http://insert_the_name_of_the_youtube_url_here
```

These three methods will download the streaming videos to your home folder (or whatever folder you happen to be in in the terminal).

---

### Post by CheeseQueen452 on 2007-04-24
I'm using the mplayer plugin in Firefox.

> **itsjustarumour said:**
> Hi,
Which app are you using to view the video streams with?

---

### Post by CheeseQueen452 on 2007-04-24
I'd rather not have to download a clip everytime I want to watch one. I have a 1ghz processor, & a cable internet connection.

> **Rhubarb said:**
> Well, sometimes I find it's just best to download the video, rather than trying to stream it in.
It could be choppy because of your processor, your internet connection speed, or the media player you choose to play the content.

---

### Post by marcosXL on 2007-04-26
> **Rhubarb said:**
> Well, sometimes I find it's just best to download the video, rather than trying to stream it in.
It could be choppy because of your processor, your internet connection speed, or the media player you choose to play the content.

So, if you want to download your videos, in a console, just type in:
```
wget http://smg.photobucket.com/albums/v2...t=MVI_1785.flv
```

If you want to download a video that uses mms:// (or sometimes an .asx playlist):
```
sudo aptitude install mimms
mimms mms://insert_the_name_of_the_url_here
```

If you want to download something from youtube:
```
sudo aptitude install youtube-dl
youtube-dl http://insert_the_name_of_the_youtube_url_here
```

These three methods will download the streaming videos to your home folder (or whatever folder you happen to be in in the terminal).

hi there, i am currently downloding from youtube the way you describe yo said,
but i have a question,, how do i download video streaming from google???

                   Thankssss.....

---

### Post by CheeseQueen452 on 2007-04-30
Well, I changed my video card & I'm still having this problem. What do I do? It seems to happen particularly at [http://music.yahoo.com](http://music.yahoo.com) . If anyone knows a solution, please help!

---

### Post by CheeseQueen452 on 2007-05-05
Well, I removed the mplayer plugin in the hopes of fixing this problem, but it's still happening. At least streaming videos still work.... I can't reinstall the mplayer plugin due to a dependancy issue. How do I get streaming videos to play without being choppy or skipping like a record? Any ideas would be appreciated! Please help!!

---

### Post by CheeseQueen452 on 2007-05-05
This issue has plagued me for about 2 months now, & no one is helping me. Doesn't anyone have a clue how to fix this? There must be something I can do!! PLEASE HELP ME!!!!

---

### Post by JimS on 2007-05-05
...
While I'm no expert in streaming videos,
it stands to reason that these videos require
a lot of ram.  And no where above do I see
any mention about ram.  I would think that
the requirement would be at least 512MB.
1GB would be better.  When I upgraded my
old Dell 4100 running at 1GHz from 128 to
512, I noticed performance improvements.

How much ram do you have?

Also, are you running any other programs
in the background while running your
streaming videos?

JimS
...

---

### Post by CheeseQueen452 on 2007-05-05
Please read my original post..... I have 512 MB of RAM, which is all my motherboard can handle. I haven't really done anything different than I did a few months ago when I didn't have this problem.

> **JimS said:**
> ...
While I'm no expert in streaming videos,
it stands to reason that these videos require
a lot of ram.  And no where above do I see
any mention about ram.  I would think that
the requirement would be at least 512MB.
1GB would be better.  When I upgraded my
old Dell 4100 running at 1GHz from 128 to
512, I noticed performance improvements.

How much ram do you have?

Also, are you running any other programs
in the background while running your
streaming videos?

JimS
...

---

### Post by JimS on 2007-05-07
....
Still see nothing about ram until your last missive.

BTW - that Swiffer ad - I heard they have a warning
not to use around small children and pets.  Apparently
they use toxic chemicals.  P&G is a big user on toxic
chemicals in their products.  Better to clean using
vinegar and water with a little tea tree oil.  But I doubt
that it is toxic chemical gases in your home that is
causing your PC problems, just human and pets.

JimS
...

---


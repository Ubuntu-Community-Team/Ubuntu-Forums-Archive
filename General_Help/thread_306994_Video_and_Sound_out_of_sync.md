---
title: "Video and Sound out of sync"
date: 2006-11-25
forum: General Help
---

### Post by furiousV on 2006-11-25
Hey guys,

On my Ubuntu Dapper Drake installed, I noticed some videos seem to get out of sync.

If I go to youtube and watch a video, it doesn't take long for sound to obviously get out of sync. Not even one minute in, sound lags behind by 1 second. It looks horrible :(

I was using Firefox at the time, using the plugins that get offered from the yellow bar that offers you to install Flash when I don't have Flash or whatever is required to play the video.

Specs:
[list][*]Dell build[*]Pentium 4 3.2GHz[*]1GB RAM[*]Radeon 9800 Pro 128 MB[*]Ubuntu Dapper Drake - latest kernel from repisitory[*]Firefox 1.5.0.8[/list]

Any ideas?

---

### Post by teumima on 2006-11-29
I have exactly the same issue.

Anyone know of a solution?

---

### Post by cronholio on 2006-11-29
It's not an Ubuntu problem but rather a general problem in Flash. It's not possible to sync it properly, maybe this will be adressed in a future release. What I can suggest is using [Keepvid]("http://www.keepvid.com") to save the videos from Youtube to disk (save files as .flv file). Then use ffmpeg2theora to sync them and convert them to OGG Theora videos:

```
sudo aptitude install ffmpeg2theora
```

```
ffmpeg2theora --sync inputfile.flv
```

---

### Post by teumima on 2006-11-29
Man

Thanks for your reply.

This solution is acceptable for nerds like you and me.

However, for normal users this is not a solution.

Ubuntu wants to be a competition to other OSs, how will it do that if users can't even watch Youtube properly?

---

### Post by cronholio on 2006-11-29
As I said, it is a Flash problem and has nothing to do with Ubuntu. AFAIK, this problem even exists in Flash for Windows. If it is really worse in Flash Player for Linux, you need to complain to [this guy.]("http://blogs.adobe.com/penguin.swf/")

---

### Post by teumima on 2006-11-29
So you're saying this issue is also in Windows?

---

### Post by cronholio on 2006-11-29
I can't tell, I hardly ever use Windows and if I do, it's certainly not to run Flash Player. All I can say is I saw the sync issue being discussed again and again for a while now (concerning different Flash Player versions for both Linux and Windows) and it is definitely a problem in Flash Player itself. If it doesn't work on whatever OS, Adobe will need to fix it.

---

### Post by teumima on 2006-11-29
Thanks for the link. They made a beta, will try it.

---

### Post by DrZuckerbrot on 2006-12-29
Hi, 
it's indeed not only a Linux Problem, it happens on XP as well. I uploaded a selfmade Video on YouTube and Sound and Video are always out of sync, no matter if I watch it on Ubuntu or Windows. 
[http://www.youtube.com/watch?v=CdDQpwAE1Y0#GU5U2spHI_4](http://www.youtube.com/watch?v=CdDQpwAE1Y0#GU5U2spHI_4)

I looked for a solution of this problem months ago and there still seems to be little knowledge of it on the web. All I found is a recommendation, that if you import your video into the Windows Movie Maker and then save it will solve the problem. Well, what solution is that?!
The Windows Movie Maker itself is a problem... it crashes already if you only say the name...
](*,)

---


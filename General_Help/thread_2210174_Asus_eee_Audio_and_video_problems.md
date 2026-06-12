---
title: "Asus eee: Audio and video problems"
date: 2014-03-09
forum: General Help
---

### Post by jeremy19 on 2014-03-09
Hi, I'm super new to Ubuntu, and have just recently installed 13.10 copy of Lubuntu on
my asus eee pc netbook. runs great with the exception of choppy audio with music files and choppy video playback as well.

any help would be appreciated "=:)

---

### Post by TheFu on 2014-03-09
I have an Asus Eee 1008h - and since the GPU doesn't have video codec support built in, only videos of DVD resolution/quality playback well on it. That means no HiDef. All video has to be decoded in software by the CPU, no hardware acceleration is possible. That explains the video issues.

Can you turn down the "cheese" for the UI?  Change from Unity to any other GUI. That will help.  XFCE or LXDE would help.

Does all audio playback poorly? Over a network or direct connection?

---

### Post by jeremy19 on 2014-03-09
Hi, 

I don't have the know how to change Unity or any of those options, without a detailed walk through, but thanks alot for your help. Pretty much all audio is choppy, mp3s and everything else...that includes streams and stored files.

---

### Post by pqwoerituytrueiwoq on 2014-03-09
Xubutnu (XFCE):
14.04 Beta: [http://cdimage.ubuntu.com/xubuntu/daily-live/](http://cdimage.ubuntu.com/xubuntu/daily-live/) (it will be final mid April)
13.10 [http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/13.10/release/)
download the ISO and do what you did when you installed ubuntu

you could just install the [xubuntu-desktop]("apt:xubuntu-desktop") meta package, but if you don't want all the ubuntu (unity) stuff installed the above links are the easy way

---

### Post by Rob Sayer on 2014-03-11
> **pqwoerituytrueiwoq said:**
> Xubutnu (XFCE):
14.04 Beta: [http://cdimage.ubuntu.com/xubuntu/daily-live/](http://cdimage.ubuntu.com/xubuntu/daily-live/) (it will be final mid April)...

Why would anyone recommend a beta ubuntu release to someone who admits they're a complete novice?  Alpha/beta releases are for the highly skilled.  *Period*.

I'm not the LXDE desktop per se is the problem anyway.

The audio definitely shouldn't be choppy.  Try installing lubuntu-restricted-extras.  I recommend synaptic for this.  It doesn't seem the easiest way at first but it's highly recommended.  Or do it in terminal:

```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```

For the video, your netbook may very likely have the intel atom 2600 cpu with the cedarview gpu.  You can check the cpu by going into menu->system tools->system profiler.  If it is the atom 2600 (like my acer netbook) I'm afraid it's not well supported in linux.  There is no hardware 3D acceleration.  You'll never get particularly great video performance with that gpu, especially with 720p or greater.

What video player are you using?  VLC is slow.  Use gnome mplayer (which came with lubuntu 13.10) or smplayer and adjust the file cache to 8192Kb.  Also add this to mplayer arguments:

```
-cache-min 30
```

---

### Post by TheFu on 2014-03-12
> **jeremy19 said:**
> Hi, 

I don't have the know how to change Unity or any of those options, without a detailed walk through, but thanks alot for your help. Pretty much all audio is choppy, mp3s and everything else...that includes streams and stored files.

So - you can have 50 different GUIs in any Linux, if you like.  So, first lets add LXDE. Open a terminal and type:
```
sudo aptitude update
sudo aptitude install lxde
```
The first line updates the list of packages - that will keep any dependencies in check. 
The 2nd line installs lxde (plus any dependencies required).

Assuming that went well - it has never failed me - next you just need to logout (no need to reboot).  LXDE is much like the XP interface, so you will be able to find your way around easily.

On the login screen, there is a gear-like thingy - click it.  That shows the different "desktop environments" or "window managers" that are available.  Unity is the default for normal Ubuntu Desktops.  Select the "LXDE" one, and login.  Bam, you are there.  You can run any of the old programs that worked before - most will be in the menu for you already.  If not, you can add them or just hit ALT-F2 and enter the command.  Much less "cheese", but still very efficient and useful.  VLC should playback any audio file without skipping and videos at 600p resolution or less should work fine.

LXDE is much lighter than Unity. If you want a side-bar, LXDE will let you make a side-panel. Not quite the same, but my 80+ yr old Mom liked it on her Pentium4.

If you don't like LXDE - you can remove it or just login using "Unity" the next time.

LXDE and Unity don't seem to harm each other's settings, but some of the DEs will, so be careful when trying out others.  It is best to create a new userid for testing each DE.  This will keep all the settings separate.

Linux is magical in that way. ;)  If this doesn't solve it - let us know and we can get ugly technical as necessary.  
Or ... if everything is fine, please mark the thread "SOLVED" - instructions are in my signature.

---

### Post by coldraven on 2014-03-12
The OP states that he has Lubuntu, why are you all talking about Unity.
I'm writing this on my eeePC 900 running Xubuntu 13.10. Streaming video is choppy but video from file is OK. Audio occasionally clips but is mostly fine, I thought that it may be badly encoded mp3s that caused this .

---

### Post by TheFu on 2014-03-13
> **coldraven said:**
> The OP states that he has Lubuntu, why are you all talking about Unity.
I'm writing this on my eeePC 900 running Xubuntu 13.10. Streaming video is choppy but video from file is OK. Audio occasionally clips but is mostly fine, I thought that it may be badly encoded mp3s that caused this .

**You are 100% correct. I confused this thread with another!  Sorry.**

Again, I have an Asus Eee 1008H with an N280 Atom CPU. It is about 4 yrs old and due for replacement.

The way that video is played back, the network connection to the video, the encoded settings from the creator and the resolution matters.
* Flash eats CPU, especially in a browser. 
* HiDef video (anything over 600p) stutters. 
* if streaming is used, larger buffers are necessary if a slower connection is available. I only have a 15/3Mbps connection and see stuttering from time to time in the evenings. Mornings and daytime, which are less busy for the ISP, work fine. I still prefer to download the entire stream first.
* VLC can playback anything I need to watch, so I use that most of the time, but it is heavier than pure **mplayer** CLI, which I also use.

For audio, I don't really see any stuttering. Everything is streamed from a local server and played back through **clementine** or vlc if I'm lazy. The only time there have been issues with audio was when the file had bad encoding. Any computer in the last 10 yrs should handle audio just fine.

Heck, I own a Nokia N800 from 2008 (very early 4" ARM tablet) and it handles any audio fine. For video, I needs frame rates to be reduced and resolution cut down, but for a cross country airplane trip, that was fine.

---

### Post by Yellow Pasque on 2014-03-14
Something to try (this has helped other Atom owner with choppy audio/video): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by Rob Sayer on 2014-03-17
> **TheFu said:**
>  ... Any computer in the last 10 yrs should handle audio just fine...

I agree, this is the slightly confusing part.  Video problems I can see, not audio.

I think the OP needs to specify which actual model/cpu/amount of RAM.

There was something I saw once on mplayer saying that on some really old machines you may need to use some codec whose name I don't remember for mp3s because the default one will get buffer underruns.  I may have a link to it on my machine at home but not this one, and I can't find it right now.  But I still don't see how that could be a problem.  Asus eee's aren't *that* old.

Unfortunately LXDE documentation stinks. They've said that's going to be remedied in lubuntu 14.04.

---


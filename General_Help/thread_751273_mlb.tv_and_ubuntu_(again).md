---
title: "mlb.tv and ubuntu (again)"
date: 2008-04-10
forum: General Help
---

### Post by bpkennedy on 2008-04-10
Ok, so I am trying to get mlb.tv to work in Ubuntu Gutsy. I have seen some old posts here and elsewhere via googling that offer solutions, but it seems like mlb.tv has switched things up to use Microsoft Silverlight. Has anyone come up with a way to get this to work? What irks me most is that I'm not even really interested in the streaming video portion, I'd just like to listen to the games, but that isn't workout out either. Any help would be appreciated, thanks!

---

### Post by trippinnik on 2008-04-10
Haha, every year it's the same thing and they seem to change the player a lot too.  I actually tried to get Moonlight running under linux.  It requires building Mono and a bunch of stuff from source, but in the end the last part failed to compile and now my mono install is foobared.  
What I'm doing recently is running windows in VirtualBox and watching the game from there.  it beats having a windows partition and rebooting just to watch the games.  But it's really the only thing I ever use windows for. Hopefully the Moonlight (mono's version of Silverlight) will catch up and MLB.tv will stay with the same version long enough for us to watch some games in Linux...

---

### Post by bpkennedy on 2008-04-10
@trippinnik , haha yeah. I have debated just firing up a vmware instance of windows xp to get games, but that sort of seems like giving up and I was wondering if anyone else had come up with a solution. Thanks for your response though.

---

### Post by trippinnik on 2008-04-10
Yeah, well here's the link for the howto I tried: [http://www.deepakg.com/blog/archives/39.htm](http://www.deepakg.com/blog/archives/39.htm)
and mono's site: [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight) If you can get it to work, let me know!

---

### Post by trippinnik on 2008-05-01
Woohoo! Found a little python script that takes care of our problems.  Check it out here: [http://www.eds.org/~straycat/mlblinux.php](http://www.eds.org/~straycat/mlblinux.php) No seeking working right now, but a lot better than booting windows or running in VM.

---

### Post by ljoslin on 2008-05-13
Thanks!  That works for me!  (This year)  no more booting into windows just to watch baseball!!  I had to do a little tweaking of the config, but otherwise it worked perfect!!

-=Ljoslin=-

---

### Post by trumpcouptimmy on 2008-05-20
I've tried mlbviewer in 8.04. After some tweaking, I actually get a half second of picture and then the picture freezes to a still. I want to keep ubuntu, but the live cd for gnome version of pclinuxos works right out of the box. What can I do to get that functionality? I want to stick with ubuntu.

---

### Post by melvis02 on 2008-05-29
Just a quick tip, in 8.04 I've had nothing but trouble with PulseAudio.  I was also having mplayer hang instantly, but if you add '-ao alsa' to your mplayer commands in the config file, it works great!

the audio and video player lines in my config looks like this, nothing special:

audio_player=xterm -e mplayer -ao alsa -cache 64 -quiet -playlist
video_player=xterm -e mplayer -ao alsa -cache 2048 -quiet

---

### Post by BigAl737 on 2008-07-19
> **trippinnik said:**
> Woohoo! Found a little python script that takes care of our problems.  Check it out here: [http://www.eds.org/~straycat/mlblinux.php](http://www.eds.org/~straycat/mlblinux.php) No seeking working right now, but a lot better than booting windows or running in VM.

I am brand new to linux (using Ubuntu). I'm not a smart enough computer guy to make MLB.TV work with Ubuntu. I've got some very basic questions. How do I install Python? What is simplejson and how do I install it? If someone good give me a step by step on how to get MLB.TV to work I really would appreciate it. Thanks very much in advance.

---


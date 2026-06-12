---
title: "Playing music directly from server....kindof..."
date: 2006-07-27
forum: General Help
---

### Post by Simpel on 2006-07-27
Hey all

I'm searching for a little nifty bit of software to install on my server. Due to several reasons I have to move my desktop computer(windows machine) so that I no longer can connect it to the stereo, in other words, i can't play music anymore. The thing though is that I can still connect my server(latest ubuntu release) to the stereo and in some smart way play music directly from that machine. So here's my question, does anyone know a good program for playing music directly of the server but control it from another computer?

I mean think of it as using winamp or something on the computer you're workning on, the only thing beeing that the sound doesn't actually come from your computer but from a server....

---

### Post by madmetal on 2006-07-27
you want to stream music from your server to the desktop pc? try VLC player [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by Simpel on 2006-07-27
nono, no streaming...I just want to be able to tell the server what to play and then the server will play it. No audio will arrive to my desktop computer so to speak!

---

### Post by stimpsonjcat on 2006-07-27
I haven't tried it myself yet, but [mpd]("http://www.musicpd.org/") looks like what you want. (together with gmpc for example)

---

### Post by Simpel on 2006-07-27
yea, saw that to, the only problem though is that it doesn't have a controller for windows....cos the thing is that I want to use windows on my desktop and linux on my server...

---

### Post by stimpsonjcat on 2006-07-27
what about [DAAP]("http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol")?
Rhythmbox supports DAAP for example, so you could run rhythmbox on your server and itunes on the windows machine.

---

### Post by it.henrik on 2006-07-27
I dont know how to do it with DAAP.. but I do know how to do this with SSH+your fav. mp3 player.

in linux you just have to ssh in to your music server with x/forwarding enabled. Like this

ssh mymp3server -X

and then start you fav mp3 player like this:

xmms&

And you will get the gui on your curretn desktop while running the aplication on the server and thereby get the sound out from the soundcard on the server.

In windows you can do the same with putty and cygwin.

Good luck.

---

### Post by Simpel on 2006-07-31
hi again

it doesn't seem to work i did what you said throug putty and it resulted in 

simpel@coppi:~$ xmms&
[1] 23437

** CRITICAL **: Unable to open display


any idea why? i did this from a windows machine...

---

### Post by Persianelfster on 2007-06-18
If these machines are connected locally from a router this will work fine.  
install openssh-server on your ubuntu machine.
type openssh-server in terminal 
download Xming for windows 
select Xlauncher
select multiwindows
select plink.exe
under apps its default is xterm, change it to rhythmbox
find your ip of your ubuntu server (terminal command is ip addr)
put your ubuntu up there, along with your normal login name and its password
hit next till it says finish, if you want you can hit save configuration and put it on your desktop, and if you click the short cut you will be prompted for your password.
With this done you will control your music files, however the music will come out of the stereo that is connected to the server.
-PersianElfster

---


---
title: "Cron: How come cron doesn't recognize sound card"
date: 2020-09-13
forum: General Help
---

### Post by themeditationcenter on 2020-09-13
I wrote an Alarm cron job. My cron is below

```
00 07 * * * export DISPLAY=:0 /usr/bin/audacious /home/user/Music/Gentlebreeze.mp3 
```


But I get this error

```
ALSA error: snd_pcm_open failed: No such file or directory
```

I tried with different music players - Elisa, VLC, Clementine and now Audacious...nothing works. Can anyone help please.

My dmesg can be found [here]("https://paste.ubuntu.com/p/zJJwvbPBKr/").
My hardware info can be found [here]("https://paste.ubuntu.com/p/NJDVhy7fxx/").

Please let me know if you need any further information from me to help resolve this issue.

---

### Post by TheFu on 2020-09-13
You can't use GUI programs with cron.  Cron doesn't tie to any session and PulseAudio requires a session unless you set it up to be run as a server, shared, by all users of the system.  There are issues in doing that, so Pulse starts only after a userid session is started, on the console, after login.

Don't use cron for any GUI programs, is the simple answer.  You could try a non-GUI player, but ensure it doesn't try to use any GUI. So, mplayer and mpv can work, but only if there isn't any GUI included inside the data to be played.  Better to use a 100%, pure, non-GUI, non-user-tied, player.

cmus is one, but it needs a login to work, since it keeps settings in some personalized directories.

---

### Post by themeditationcenter on 2020-09-13
So this is something which started in this new Ubuntu version?
For this used to work for me in earlier version (I guess 18.04 or below), this happened after I upgraded to 20.04.

---

### Post by TheFu on 2020-09-13
> **themeditationcenter said:**
> So this is something which started in this new Ubuntu version?
For this used to work for me in earlier version (I guess 18.04 or below), this happened after I upgraded to 20.04.

In never should have worked. It is a huge, huge, security failure.

---

### Post by themeditationcenter on 2020-09-13
Thank you for educating me, much appreciated. I'll try to use cvlc (the command line of vlc) and try out. Or will see if I can get it through a shell script or a python script.

---

### Post by TheFu on 2020-09-13
> **themeditationcenter said:**
> Thank you for educating me, much appreciated. I'll try to use cvlc (the command line of vlc) and try out. Or will see if I can get it through a shell script or a python script.

Perhaps it is just me, but I once installed cvlc and could never get back to the normal GUI for VLC again on that system.  At the time, I barely used vlc, so it wasn't something i tried to solve after 30 seconds.  

I have a little script that lets me search for music playlists (m3u files) across lots of storage here using partial regex patterns.  If there are multiple matches, the list is displayed and a number from the list has to be entered to play that list of tracks.  The player used is mpv. It can also randomize an playlist.

```
$ m-search classic
...
8: /R/Music/Classical/Classical_all-random.m3u
...
8<enter>
 Artist: Bach, J.S.
 Genre: Classical
 Title: Air_on_the_G_string
```
This works over an ssh connection or locally on the system. The music is on NFS storage available to most systems here.
Sunday morning is a good time for some classical music. ;)

For alarms, I'd use a tablet or phone, since I may not be logged into the system when it is time.

I can post the script somewhere, if you like. It was something I hacked together in about 30 minutes, so it is full of problems and not really safe for use by the world at large.

---

### Post by themeditationcenter on 2020-09-14
Thank you very much, no words for going up and beyond for helpding me, yes please if you can share the code it would be of great help.

I installed KAlarm and solved my current issue.

cvlc is installed by default when you install vlc.

---

### Post by TheFu on 2020-09-14
[https://paste.ubuntu.com/p/MGy5dXCqzc/](https://paste.ubuntu.com/p/MGy5dXCqzc/)

t will need some changes.  You can't use HOME under cron, for example.

---


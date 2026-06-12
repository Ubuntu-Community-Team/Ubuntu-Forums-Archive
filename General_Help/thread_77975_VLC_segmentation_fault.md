---
title: "VLC segmentation fault"
date: 2005-10-17
forum: General Help
---

### Post by M4l3k on 2005-10-17
Hi all,

HEre is what I got when trying to stream an avi file through the network via UDP:

user@server:~$ vlc
VLC media player 0.8.4-svn20040920 Janus
Segmentation fault

This occurs just after I have loaded the file to stream, selected the streaming options and clicked OK!

Any help or sugegstions here?

THanks

M4l3k

---

### Post by yama on 2005-10-21
Same problem here ! Whereas I can play anything without problems, UDP streaming causes vlc to crash.

---

### Post by Kyral on 2005-10-21
I recall seeing a bug about this in Malone. Make sure you have all the libraries you need for VLC installed

---

### Post by rklauco on 2005-12-06
Did anyone solve this?
I achieve this problem everytime I try to stream over UDP.
I have all the codecs needed.

Any help?

Thanks in advance.

---

### Post by stevea1210 on 2005-12-17
I'm haveing the same issue.  I can play any file directly in vlc, but if I try to stream the file, it segfaults.  I have tried it on three different ubuntu pc's,  all running vlc 8.4.  I have been able to open a udp stream coming from a windows pc.  Has anyone solved this yet?

---

### Post by neo_reloaded on 2006-07-11
Hi,
I installed vlc playere by:
sudo apt-get install vlc vlc-plugin-esd

I get following error when I run as normal user
~$ vlc
VLC media player 0.8.4 Janus
Segmentation fault


But if I run as super user - ie; 
sudo vlc, I can run vlc!

What is going on? anybody has got VLC up and running on dapper ?
TIA
-rc
------------------------------

Ubuntu Dapper drake on Thinkpad t42p

maximus@prometheus:~$ uname -a
Linux prometheus 2.6.15-26-386 #1 PREEMPT Fri Jul 7 19:27:00 UTC 2006 i686 GNU/Linux

---

### Post by stevea1210 on 2006-07-11
Try removing both VLC and the audio plugin, and then reinstall just VLC.  That way we can see if the plugin is causing the issue.  

I am able to run vlc in dapper on several machines fine.  IS this a clean dapper install, or is it breezy to dapper upgrade?

**disclaimer:  Based on your post it looks like your just trying to launch the player, not trying to stream as this thread was originally talking about.  Please let me know if that is incorrect.

---

### Post by neo_reloaded on 2006-07-14
Hi, I am trying to just run the player.
This is a clean dapper installation.
Thanks!

---

### Post by zaiyon on 2006-07-16
Same issue here.
But for me, VLC segfaults always, also as superuser, at the program startup.
I have vlc, and his dependencies wxvlc and vlc-plugin-alsa installed.

Dapper install (no upgrade) using prelink which could be the cause.
Are you using prelink too?

---


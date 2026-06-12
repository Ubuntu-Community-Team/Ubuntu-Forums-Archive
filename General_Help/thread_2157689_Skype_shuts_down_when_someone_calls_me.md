---
title: "Skype shuts down when someone calls me"
date: 2013-06-26
forum: General Help
---

### Post by gugu88 on 2013-06-26
Hi everybody,

I have a problem with skype 4.2.0.11 on ubuntu 12.04 64 bit. Every time I receive a call (either video or normal call) as soon as I answer skype shut down!!! If I make the call it works without problems until the notification of some contact connecting/disconnecting appears on the bottom on the right side of the screen. 

I tried several skype version but the problem persist!!!

With ubuntu 10.04 64 bit I have never had any problems skype always worked just fine!!!

What I can do?? 

If I launch skype from a terminal it gives the following message:
```
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters CARD=Intel
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default:CARD=Intel
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default
skype: hcontrol.c:326: _snd_hctl_find_elem: Assertion `hctl && id' failed.
Aborted (core dumped)
```
The first two lines appear as skype is launched the others appear when I answer a call or one of my contacts connects!!!

Thanks in advance for your help.

P.S: sorry for my terrible english!!

---

### Post by scbingham on 2013-06-27
I suffered similar problems too. Out of frustration I uninstalled skype & installed v2.2 (I think). That seemed to work.
I have noticed that my skype has upgraded to 4.2.0.11. I think it works; haven't used it for so long.

If you search the forums, there are threads on this very topic, I can't remember exactly where though.

Good luck.

---

### Post by gugu88 on 2013-06-27
I have already tried to install v 2.2, It did not show the same problem but it did not recognize my microphone which worked perfectly with sound recoder or other skype version. I have already searched in the forum and tried to follow some solution but i did not solve the problem!!!!

---

### Post by scbingham on 2013-06-27
Not sure then, I'm afraid. Maybe ask the moderators to move this to General Help, you'll probably reach a wider audience.
Click on 'Report Post'

---

### Post by artbio on 2013-06-27
Check if you have the file "libasound_module_conf_pulse.so" under directory "/usr/lib/x86_64-linux-gnu/alsa-lib/". If you don't have it install libasound2-plugins. I am not sure if you also need the i386 version. Since Skype is not a 64 bits app.

---

### Post by cariboo on 2013-06-27
Moved by request.

---

### Post by gugu88 on 2013-06-27
@artbio i have the file "libasound_module_conf_pulse.so" in the right directory. I don't know if it is 32 or 64 bit version, how do i check??

However my skype just crushed even if i wasn't in a call!!!! I was just chatting whit a friend of mine and the program stopped working!! It asked me if i wanted to force quit, i pressed force quit but skype didn't shut down!!
I had to use ```
sudo kill -9 process_pid
```
Terminal from which i launched skype told me ```
gugu@guido-nb:~$ skype
ALSA lib conf.c:4687:(snd_config_expand) Unknown parameters CARD=Intel
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default:CARD=Intel
*** glibc detected *** skype: corrupted double-linked list: 0xe24b89a0 ***
^[^GKilled
gugu@guido-nb:~$
``` I don't know if that has anything to do with the call's problem, anyway with ubuntu 10.04 none of this problems ever happened!!

---

### Post by scbingham on 2013-06-27
None of these problems appeared until after M$ bought skype, problems aren't just limited to ubuntu but android, ios, etc.

---

### Post by gugu88 on 2013-06-28
It could be but however i have friends who are able to use skype on ubuntu without any problem. I don't know on android but on iOS skype works perfectly.

No ideas?

---

### Post by kotov2 on 2013-08-28
Some ideas presented here: [http://community.skype.com/t5/Mac/Debian-7-0-Skype-crashed-when-making-call/td-p/1371149](http://community.skype.com/t5/Mac/Debian-7-0-Skype-crashed-when-making-call/td-p/1371149)
Installing libasound2-plugins:i386 seems to work

---


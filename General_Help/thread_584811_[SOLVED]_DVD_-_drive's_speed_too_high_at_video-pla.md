---
title: "[SOLVED] DVD - drive's speed too high at video-playback!"
date: 2007-10-21
forum: General Help
---

### Post by perixx on 2007-10-21
Hello again!


I have a really annoying problem with my DVD-drive not slowing down while playing DVD's - other than with Audo-CD's, it keeps running at full speed all the time, which causes unbearable background noise...

I tried the following without any result: 

setcd -x4 /dev/hdc
sudo eject -x4 /dev/hdc
sudo hdparm -E8 

I also used other speed factors, which should work for my drive - still no luck!

PLEASE HELP !


perixx

---

### Post by UK-Wobbie on 2007-10-21
> **perixx said:**
> Hello again!


I have a really annoying problem with my DVD-drive not slowing down while playing DVD's - other than with Audo-CD's, it keeps running at full speed all the time, which causes unbearable background noise...

I tried the following without any result: 

setcd -x4 /dev/hdc
sudo eject -x4 /dev/hdc
sudo hdparm -E8 

I also used other speed factors, which should work for my drive - still no luck!

PLEASE HELP !


perixx

It sounds like it's your CD drive not Ubuntu it self!
If you put a Ubuntu CD or a game CD in the drive is it still going full speed?
It may be your drive that is dieing or it may be that your CD drive is not installed right!

I no allot  of people are having problems with CD drives!

---

### Post by perixx on 2007-10-22
I cannot say for games, but even before I installed any of the mentioned software, I could play Audio CD's in a silent slow mode...

Besides, in Windows there are programs like 'CD-Bremse' that can control this drive..!


perixx

---

### Post by perixx on 2007-11-03
Heelllooo!


Is there anybody that can provide a solution ? My ears are being seriously damaged ^^!!


perixx

---

### Post by blue46 on 2007-11-03
yea,  is there something like nero-speed   for ubuntu?    i just want to be able to play a DVD movie with 1x speed  in Ubuntu?    is it really so complicated??  do i have to rebuild the kernel or what?    hdparm doesnt work:(   my DVD drive is NEC.

---

### Post by perixx on 2007-11-03
OMG only too true... perhaps there's some tool for KDE where you have to recompile it from source and add some 50MB to the system ?? 

;-((


perixx

---

### Post by perixx on 2007-11-04
*bump*

---

### Post by perixx on 2007-11-04
*bumpagain*

---

### Post by newman on 2007-11-06
bump

---

### Post by perixx on 2007-11-06
thx for co-bumping, newman :}

---

### Post by newman on 2007-11-17
no problem
bump:)

---

### Post by spinifex on 2007-11-17
Bump ... :)

I'm having same trouble.   ears are ringing whilst my ASUS DVDRW goes flat out.  

I have tried [_this link_]("http://wiki.linuxquestions.org/wiki/Quieting_linux") but the settings dont stick.  Try reboot and I lose it all.  

I'd love some tips to get this up and running properly as I think this points things in the right direction. 


I have also been stuffing around with this:  hdparm -E 128 /dev/scd0  where -E 128 = "about the slowest I am told I can go with my cd drive, and /dev/scd0 is the device I want to change the speed on.    

Only problem is that scd0 is sim linked to sc0 in my /dev ... and I also have cdrw, cdrom, dvd & dvdrw.  Someone chuck me a bone here! It dosnt seem right for some reason.   There has to be one all encompasing setting to slow my optical drive speed down somehow?   hence the reference to scd0 ( got me muddled...  

there is also all this stuffing around:

[root@localhost ~]# eject -x 4 /dev/cdrom
[root@localhost ~]# eject -x 4 /dev/dvdrw
[root@localhost ~]# eject -x 4 /dev/sdc
eject: unable to find or open device for: `/dev/sdc'
[root@localhost ~]# Set-cd-rom-speed
-bash: Set-cd-rom-speed: command not found
[root@localhost ~]# Set-dvd-rom-speed
-bash: Set-dvd-rom-speed: command not found

but you can see that didnt get me very far.

Can anyone clear this up?

---

### Post by newman on 2007-11-18
OK, issuing the command "setcd -x 2" in a terminal did the trick, but how can I make it permanent so I don't have to re-type it every time I retart the Computer?:confused:

---

### Post by perixx on 2007-12-12
Allright Newman, 

here's my little **'HowTo: set the DVD-speed automatically'** - thank you for the hint on 'setcd' again! I've tried this one before and it DID work for audio-CD's, but not for DVD's - I didn't know why. Now I've looked into it again and via the '--help' command I saw, that there's an optional [device] parameter!

So I finally figured out that I had to use the parameter for my DVD device (/dev/dvd) in order to slow it down during video-playback. Since I don't know any other solution to have the slowdown-command active each time I insert a new DVD, I made a bypass via some tiny script that sets the drive-speed and loads my videoplayer (SMplayer):
```
#! /bin/bash

setcd /dev/dvd -x 2
/usr/bin/X11/smplayer
```

Of course, I had to install 'setcd' first, with the terminal-command
```
sudo apt-get install setcd
```

Now, all I needed to do was to create a starter on my panel-bar, pointing to that script-file (which needed to be set 'executable', of course).

Et voilà!

perixx

---

### Post by perixx on 2007-12-12
**Addition:**

For autoplay-functionality you'll have to specify CDrom- and DVD-devices in Thunar:
> Preferences/Advanced/'RemovableMediaManager'/'EntertainmentMedia':
Audio CD's: /usr/bin/X11/smplayer cdda://0
DVD's: /home/USER/scripts/silentDVD_autoplay

For Audio-CD's there's no need for a slowdown-parameter; CD's are being played at a decent speed by default.
For DVD's autoplay, I used a script similar to the one I posted before, content:
> #! /bin/bash

setcd /dev/dvd -x 2
/usr/bin/X11/smplayer dvd://1

Unfortunately, MPlayer's '-speed' parameter doesn't work, so using 'setcd' seems to be indispensable.

perixx

---


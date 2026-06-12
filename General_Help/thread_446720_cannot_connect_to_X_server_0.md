---
title: "cannot connect to X server :0"
date: 2007-05-17
forum: General Help
---

### Post by msak007 on 2007-05-17
I'm having a problem in Kubuntu Feisty that's driving me nuts. It just recently started (I'd say within the past week) where all of a sudden, with no warning, I can't open _***ANY***_ applications at all. At first I thought it was due to Cedega running fullscreen, because sometimes it'd freeze and I'd have to ALT+Fx to switch to another tty and kill the process, then switch back. But I did that 2 days ago and then I had problems launching apps immediately afterward. I turned my comp off before leaving for work last night, turned it on this morning, and started using it as normal. The only thing I did was run Adept Updater to grab the updates, and went about checking my email. Then while reading RSS feeds (about 20 minutes after the initial bootup), I noticed clicking links wasn't doing anything. I tried to launch Firefox from the terminal, and this is what I get:

(firefox-bin:30666): Gtk-WARNING **: cannot open display:

Firefox is really the only GTK app I run, everything else is KDE and this is what I get when trying to launch any other app (such as Konqueror):

konqueror: cannot connect to X server :0

Restarting the X server or rebooting fixes the issue, but that's a pain and I'm not sure why this started happening or what's causing it (if it's anything I'm doing). I tried a search and most peoples' problems ended up being related to kdesu or running an app as root, or starting kdm to launch the X server. I'm already in KDE, just trying to run the apps as myself. If anybody can confirm this issue or point me to an existing bug, or any possible solutions or workarounds, I'd be grateful.

* As a side note, any search for this specific error in the forums gives me an error that both X and :0 are too short of search terms and won't return any results. I did the best I could using part of the error message and also Google.

---

### Post by fanatik on 2007-05-17
i'd guess it has something to do with your .Xauthority file - can you show the output of:

$ ls -l ~/.Xauthority

also take a look at man xauth, it might help. sorry not to be of more help.

---

### Post by msak007 on 2007-05-17
I thought about that too, but I already have read / write access to my file:

```
 -rw------- 1 motasim motasim 308 2007-05-17 09:48 /home/motasim/.Xauthority
```

This is after a reboot though (when it starts working again), so I'll check it when it stops working again (hopefully it won't).

---

### Post by msak007 on 2007-05-18
Well it happened again. This time I left my comp on overnight while I was at work, came back home this morning, and started reading my email. Once again clicking on links doesn't start Firefox, and I get the same output through the terminal. I did check the permissions on .Xauthority and they were the same. The only apps I had running overnight (excluding background services and NetworkManager) were Kontact (email / RSS icons in the systray) and KTorrent. If anybody else has any ideas or solutions I'm all ears.

---

### Post by fanatik on 2007-05-18
another thing you can check is your hostname. i'm sure i've had probelms in the past where i couldnt start apps due to the hostname or dns lookups or something similar...can't quite remember exactly though. sorry.

---

### Post by 13u11fr09 on 2007-05-18
> **msak007 said:**
> Well it happened again. This time I left my comp on overnight while I was at work, came back home this morning, and started reading my email. Once again clicking on links doesn't start Firefox, and I get the same output through the terminal. I did check the permissions on .Xauthority and they were the same. The only apps I had running overnight (excluding background services and NetworkManager) were Kontact (email / RSS icons in the systray) and KTorrent. If anybody else has any ideas or solutions I'm all ears.

this is just a random thought, but I wonder if you're running out of memory and the [OOM killer]("http://lwn.net/Articles/104179/") is killing the processes that these programs require...  try looking at `top` when this seems to be happening.  Is your swap used up? 

if this is the case, than more than likely one of the apps you're running overnight has a memory leak.

---

### Post by msak007 on 2007-05-18
> **fanatik said:**
> another thing you can check is your hostname. i'm sure i've had probelms in the past where i couldnt start apps due to the hostname or dns lookups or something similar...can't quite remember exactly though. sorry.

My hostname is fine, and I already checked both the hosts and hostname file. Nothing's changed.

> **13u11fr09 said:**
> this is just a random thought, but I wonder if you're running out of memory and the [OOM killer]("http://lwn.net/Articles/104179/") is killing the processes that these programs require...  try looking at `top` when this seems to be happening.  Is your swap used up? 

if this is the case, than more than likely one of the apps you're running overnight has a memory leak.

I run top all the time because I'm always in the terminal, and also because when this happens I can't launch KSysGuard. I've never seen anything eat up my memory / CPU. I have 1 GB of RAM, and the most I've seen is when I have a ton of applications running Xorg itself uses 10-15%.

EDIT: The only way I'm in the terminal is because Yakuake is running in the background all the time. Otherwise I wouldn't be able to do anything like launch Konsole because I can't launch new apps, only use existing apps that are already running.

---

### Post by msak007 on 2007-05-20
Anybody else have some insight or suggestions? Possibly any log entries that might help? I'm getting kinda desperate here and will have to resort to a format / reinstall if I can't get this fixed. It happened again, except this time I left my comp online without any of my normal apps running, so I kinda narrowed it down now to something running in the background. I captured the output of all the processes running when the comp first started, the processes running just before a reboot due to this problem, and a difference of the two. If anyone else can help please let me know.

---

### Post by hendrikvanantwerpen on 2008-07-01
I don't know if you solved the problem already, but to give googling people a hand. In some way the authentication for localhost is lost. By running
$ xhost +YOURHOSTNAME
it starts working again (this of course only works if you have a terminal still open). In my case this always happen after the gnome-screensaver has been active (sometimes the unlock window doesn't even appear). Still looking if I can find a more stable solution.

---

### Post by rhk on 2008-07-10
Running Hardy & Kubuntu:
Sometimes programs just stop starting. When I try it from Terminal I get:

kurppa@lanka:~$ kpdf
No protocol specified
kpdf: cannot connect to X server :0
kurppa@lanka:~$ konqueror
No protocol specified
konqueror: cannot connect to X server :0
kurppa@lanka:~$

so this still exists more or less.. Logging out and in again solves it..

Any tips?

r

---

### Post by elwell642 on 2008-07-16
Hi all,

  I'm using Hardy and LTSP 5.  I'm experiencing a similar problem to others here.  (It's suprisingly difficult to google for this one! =))

  Seemingly randomly, various thin client users suddenly cannot open new X apps.  If they happen to have a terminal window up, I've tried having them run the same program from there, but it returns errors similar to what is described in this post.  Here are some examples courtesy of my ~.xsessionerrors file:

Failed to open display
/usr/lib/openoffice/program/soffice.bin X11 error: Can't open display: localhost:13.0

** (/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper:28089): WARNING **: cannot open display: 

(pidgin:28923): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed

(thunderbird-bin:31691): Gtk-WARNING **: cannot open display: localhost:26.0


  Another really strange thing about this is that if that user waits for a seemingly arbitrary amount of time (let's say around 10-15 minutes as a rough estimate), things just "start working" again!

  It's really weird and very frustrating for users.  The only non-waiting solution I've found is logging them out and then back in again.

  Any ideas?  Thanks for your help!

---

### Post by elwell642 on 2008-07-21
Hi again.  I'm not sure if this helps as a piece of the puzzle, but I notice that trying to open a window while the bug is happening won't work, BUT if I change the command to be "ssh <same machine> <same command>", it DOES work.

For example, on our system called "Eve", if I'm suddenly unable to open xeyes ;), I can write "ssh eve xeyes" and it will work.

I notice that the output of "env" is different in the two cases ('env' vs 'ssh eve env').  I put the output without using the 'ssh eve' prefix into a file called "no-ssh" and the outwith with using the 'ssh eve' prefix into a file called "yes-ssh".  Here's the output of a diff:

```

hallmant@eve:~/tmp$ diff -u no-ssh yes-ssh 
--- no-ssh	2008-07-10 09:16:50.000000000 -0400
+++ yes-ssh	2008-07-10 09:17:02.000000000 -0400
@@ -1,35 +1,14 @@
-SSH_AGENT_PID=1296
-GPG_AGENT_INFO=/tmp/seahorse-Q2USFO/S.gpg-agent:1312:1
 SHELL=/bin/bash
-TERM=xterm
-XDG_SESSION_COOKIE=7cf7f00737f55c49846929ba483dc63f-1215686230.258490-1166615946
-SSH_CLIENT=192.168.0.130 37027 22
-GTK_RC_FILES=/etc/gtk/gtkrc:/home/hallmant/.gtkrc-1.2-gnome2
-WINDOWID=46148680
-OLDPWD=/var/spool/check-reader
-PULSE_SERVER=tcp:192.168.0.130:4713
+SSH_CLIENT=192.168.0.7 52014 22
 USER=hallmant
-LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
-SSH_AUTH_SOCK=/tmp/keyring-mRTOTI/ssh
-GNOME_KEYRING_SOCKET=/tmp/keyring-mRTOTI/socket
-SESSION_MANAGER=local/eve:/tmp/.ICE-unix/1303
-LTSP_CLIENT=192.168.0.130
-ESPEAKER=192.168.0.130:16001
-PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/hallmant/bin:/usr/local/sbin
 MAIL=/var/mail/hallmant
+PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
 PWD=/home/hallmant
 JAVA_HOME=/usr/lib/jvm/java
 LANG=en_US.UTF-8
-HISTCONTROL=ignoreboth
+SHLVL=1
 HOME=/home/hallmant
-SHLVL=2
-GNOME_DESKTOP_SESSION_ID=Default
 LOGNAME=hallmant
-SSH_CONNECTION=192.168.0.130 37027 192.168.0.7 22
-DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-TH0ik27DsZ,guid=f8ad8be503446d36e21c8bee4875e658
-LESSOPEN=| /usr/bin/lesspipe %s
-CVSEDITOR=nano
-DISPLAY=localhost:11.0
-LESSCLOSE=/usr/bin/lesspipe %s %s
-COLORTERM=gnome-terminal
+SSH_CONNECTION=192.168.0.7 52014 192.168.0.7 22
+DISPLAY=localhost:20.0
 _=/usr/bin/env

```

I don't know if that's helpful for anyone, but I'll post here again if I solve this.  Please do the same =)

---

### Post by rhk on 2008-07-22
> **msak007 said:**
> 
EDIT: The only way I'm in the terminal is because Yakuake is running in the background all the time.

Funny that you mention it, I'm running yakuake all the time as well.. Maybe it has something to do with it.. I'll restart & try without it to see if there's any change on the behaviour..

(After about 90 minutes of having the computer on I got again:
kurppa@lanka:~$ No protocol specified
No protocol specified
Warning: Unable to open display ':0'.  You will not be able to display graphics on the screen. )


Are you running nvidia drivers:
[https://bugs.launchpad.net/ubuntu/+bug/116971](https://bugs.launchpad.net/ubuntu/+bug/116971)

I have ati running on vesa driver


I also filed a bug: [https://bugs.launchpad.net/ubuntu/+bug/250712](https://bugs.launchpad.net/ubuntu/+bug/250712)

r

---


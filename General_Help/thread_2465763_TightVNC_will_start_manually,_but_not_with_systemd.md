---
title: "TightVNC will start manually, but not with systemd"
date: 2021-08-10
forum: General Help
---

### Post by nate5 on 2021-08-10
Hey everyone.  I've got Ubuntu server installed on an RPi4.  I installed TightVNC, and when I run it manually, using the vncserver command, it starts up just fine, and I can connect, no problem.  But when I try to configure it with systemd, it is giving me errors. Saying the password is too short.  But vnc truncates passwords past 8 characters, and anyway I tried a longer password, and that doesn't seem to be the problem.  Here is my systemd file:

```
[Unit]Description=TightVNC server
After=syslog.target network.target


[Service]
Type=forking
User=root
#PAMName=login
PIDFile=/root/.vnc/%H:1.pid
ExecStartPre=-/usr/bin/vncserver -kill :1 > /dev/null 2>&1
ExecStart=/usr/bin/vncserver
ExecStop=/usr/bin/vncserver -kill :1


[Install]
WantedBy=multi-user.target
```

And here is the output from systemctl status:
```
&#9679; vncserver.service - TightVNC server     Loaded: loaded (/etc/systemd/system/vncserver.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2021-08-10 23:33:19 UTC; 23min ago
    Process: 6053 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=2)
    Process: 6057 ExecStart=/usr/bin/vncserver (code=exited, status=1/FAILURE)


Aug 10 23:33:19 ubuntu systemd[1]: Starting TightVNC server...
Aug 10 23:33:19 ubuntu vncserver[6053]: Can't find file /root/.vnc/ubuntu:1.pid
Aug 10 23:33:19 ubuntu vncserver[6053]: You'll have to kill the Xtightvnc process manually
Aug 10 23:33:19 ubuntu vncserver[6057]: You will require a password to access your desktops.
Aug 10 23:33:19 ubuntu vncserver[6062]: Password: Password too short
Aug 10 23:33:19 ubuntu systemd[1]: vncserver.service: Control process exited, code=exited, status=1/FAILURE
Aug 10 23:33:19 ubuntu systemd[1]: vncserver.service: Failed with result 'exit-code'.
Aug 10 23:33:19 ubuntu systemd[1]: Failed to start TightVNC server.



```

journalctl doesn't seem to give much more info.  Any ideas?

---

### Post by TheFu on 2021-08-11
Isn't vnc tied to a user session?  There aren't any user sessions until a user logs in or steps at taken to create one virtually. Running as root, which is what systemd will do by default is a bad idea and I'm guessing that the error message is telling you that above.

In my mind, all VNC tools have been replaced by NX solutions for the last 8+ yrs.  Check out **x2go**.  It is more efficient and more secure and RDP or VNC.  I have no idea whether it has been ported to ARM.  NX is ssh+a highly optimized VNC solution. Feels 2-3x faster than the other options (except straight ssh as Herman said below).

BTW, the location for PID files is typically /var/run/

---

### Post by HermanAB on 2021-08-11
VNC is mostly a Windows thing and is the ideal way to get your computer hacked. As mentioned above, VNC remotes a running user session.  You will have better luck with SSH.

---

### Post by nate5 on 2021-08-11
Yeah I definitely plan on using ssh for most things.  However I want to install handbrake on it, and feel like the gui would be best when I want to use handbrake.  I may be able to mount a monitor, mouse, and keyboard near the machine, but the plan was for it to mostly be headless, back in my A/V closet.  So VNC was mostly for the days I want to access the desktop to use handbrake.  And yes, I hadn't thought about the fact that it is a user based app, so maybe I'll just need to start it manually via SSH if I ever need to use the gui at all.  Also, I don't plan on allowing access to VNC from outside my network, so that port wouldn't be forwarded to my machine.  I would only access it from inside my network.  Thanks for the replies.

Edit: Sorry, I just realized I didn't even mention what this machine was for.  This RPi is just a POC box that I'm messing around with while I wait for parts to come in.  I'm building a new Plex Server, intel based, and plan on running it on Ubuntu server, and wanted Handbrake on it to encode some videos occasionally.

---

### Post by TheFu on 2021-08-11
Whoa there buckaroo.  Are you seriously thinking that handbrake will ever finish a transcode on any raspberry pi?  

I hate to be the bearer of bad news, but plan for a 15 minute transcode on a 12000 passmark system to take overnight on any r-pi, perhaps longer. Just for fun, have you tried using ffmpeg already to do a simple transcode to get an order of magnitude estimate?

R-pi systems (I have 2) are good for playback, not for content creation that needs any sort of transcoding or encoding.

For trancoding, I use a Ryzen 2600.  Prior to that, I used a first gen Core i7 which was very slow in comparison.  I'm going to be building a new Ryzen (almost ordered the main parts yesterday) and that will have a 3700X on a Asus B450 MB and whatever RAM I have laying around. The local retailer just dropped the prices $60 on the CPU and when paired with a MB, another $20 off. Everything else will be taken from the two other systems it is replacing - a Pentium and a Core i5.  Haven't decided if the newer machine will get put into transcoding work or not. I'm creating a failover system for a virtual machine host, so they will use shared block storage between those to systems. The hard part will be getting all the disks and disk arrays here connected to fewer systems.

BTW, I don't know how to or whether it is even possible to get GPU-based transcoding working on Linux with a stable setup.  I've read about efforts to make that happen, but they always wanted a $400 GPU, which will be more than this total system costs to build.

Anyway, run an ffmpeg tonight on an input file you hope to transcode so you understand that isn't what a r-pi is good at ... ever.

---

### Post by nate5 on 2021-08-12
> **TheFu said:**
> Whoa there buckaroo.  Are you seriously thinking that handbrake will ever finish a transcode on any raspberry pi?  

I hate to be the bearer of bad news, but plan for a 15 minute transcode on a 12000 passmark system to take overnight on any r-pi, perhaps longer. Just for fun, have you tried using ffmpeg already to do a simple transcode to get an order of magnitude estimate?

R-pi systems (I have 2) are good for playback, not for content creation that needs any sort of transcoding or encoding.

For trancoding, I use a Ryzen 2600.  Prior to that, I used a first gen Core i7 which was very slow in comparison.  I'm going to be building a new Ryzen (almost ordered the main parts yesterday) and that will have a 3700X on a Asus B450 MB and whatever RAM I have laying around. The local retailer just dropped the prices $60 on the CPU and when paired with a MB, another $20 off. Everything else will be taken from the two other systems it is replacing - a Pentium and a Core i5.  Haven't decided if the newer machine will get put into transcoding work or not. I'm creating a failover system for a virtual machine host, so they will use shared block storage between those to systems. The hard part will be getting all the disks and disk arrays here connected to fewer systems.

BTW, I don't know how to or whether it is even possible to get GPU-based transcoding working on Linux with a stable setup.  I've read about efforts to make that happen, but they always wanted a $400 GPU, which will be more than this total system costs to build.

Anyway, run an ffmpeg tonight on an input file you hope to transcode so you understand that isn't what a r-pi is good at ... ever.

Sorry, I probably posted my edit after you read my post.  I failed to mention that this RPi system was just a POC Plex system to test some things on while I waited for parts to come in for my actual Plex build.  I didn't actually plan on doing any encoding or anything on the Pi.  Just trying to play around with it, wanted to see if I could just install Handbrake on it, mess with samba, really just to mess around while I wated.  I'm actually going to be running it on an Intel i5 10400, that has QSV.  Actually just finished building it today. (short of needing to buy a new CPU cooler because the stupid stock one wouldn't clip in all the way).  16GB ram, 128gb ssd for the os and apps.  6TB WD blue drive for content.  

But yeah my Pi system didn't even seem to want to finish installing Handbrake, let alone do anything with it lol.  I was only mentioning handbrake as a reason why I wanted to use VNC on a box where I'll mostly be administering via SSH.

---

### Post by TheFu on 2021-08-12
Handbrake is a very specific sort of tool.  If you want to remotely admin a linux system, use ssh or ssh with X11 forwarding enabled. Then almost any non-GPU program can be used remotely. No need for VNC or a freakin' entire desktop. That's just crazy.

To see it work, run 
```
ssh -X userid@pi-IP command
```
Wait about 2 seconds and the window for the "command" program will be displayed locally using the X/Server on the machine you sit at.  This has been a standard part of Unix for ?30-40? yrs?   If you like pain, you can even have a movie playback over this connection. For example:
```
ssh -X mypi mpv /d/D1/M/Predator.dvd.mkv
```
While it will work, it is not the best way. I'd actually play it over an NFS mount (I make NFS mounts match local mounts for media and my sanity):
```
mpv /d/D1/M/Predator.dvd.mkv
```

There's something bad about samba when compared to NFS when it comes to video streaming.  Samba routinely stutters where NFS doesn't. For other uses, performance of each is similar, unless the newest NFS is used which can easily open 20 connections to the NFS server and transfer data much faster than samba.  I only use 4 connections here.  This is part of a full NFSv4 implementation, so people buying home, commercial, NAS probably get stripped down NFS servers.

For a plex server, your new box is overkill. I use a 2015 Pentium dual core, 8G RAM, with 32TB of storage and it runs 2 VMs along with mpd, Plex and Jellyfin media servers. Jellyfin is a replacement for plex that doesn't ship our information out.  It also runs nextcloud, calibre, wallabag servers and is the NFS server for most media on the network.  Oh, and it is my OTA TV recording system too with 4 network tuners (hdhr quad).

My Pentium box, right now:
```

top - 22:36:26 **up 18 days**, 20:38,  4 users,  load average: 0.22, 0.17, 0.22
Tasks: 272 total,   2 running, 189 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  3.6 sy,  0.7 ni, 93.4 id,  0.3 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem :  7591624 total,  **3581580 free**,  2506056 used,  1503988 buff/cache
KiB Swap:  3780604 total,  2152956 free,  1627648 used.  4759428 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND   
20323 thefu     22   2   38632   4324   3812 S   6.6  0.1   0:00.75 wget      
 1466 root     -51   0       0      0      0 S   4.0  0.0 301:36.14 irq/16-eth1
 3746 libvirt+  20   0 2637164 986.0m   3936 S   2.6 13.3   1631:09 qemu-system-x86
 2065 mpd       20   0 1319112  37540  13228 S   1.7  0.5  12:31.22 mpd       
 7048 mpd       20   0  785180  16104  12180 S   1.3  0.2   0:36.85 pulseaudio
   18 root      20   0       0      0      0 R   0.7  0.0  96:13.75 ksoftirqd/1
   30 root      25   5       0      0      0 S   0.7  0.0 236:31.16 ksmd      
20325 thefu     20   0   41916   3784   3116 R   0.7  0.0   0:00.07 top       
   10 root      20   0       0      0      0 S   0.3  0.0  84:45.03 ksoftirqd/0
  400 plex      20   0 1764228 195660   4348 S   0.3  2.6  33:53.34 Plex DLNA Server

```
Mostly idle.  A TV show is being recorded (wget) and a VM was doing something and the music server (mpd) is playing to another room. Neither Plex nor Jellyfin isn't being used.  It has been up 18 days, so a very stable system.

With plex streaming content to the projector setup, it isn't much different.

---

### Post by nate5 on 2021-08-12
> **TheFu said:**
> Handbrake is a very specific sort of tool.  If you want to remotely admin a linux system, use ssh or ssh with X11 forwarding enabled. Then almost any non-GPU program can be used remotely. No need for VNC or a freakin' entire desktop. That's just crazy.

To see it work, run 
```
ssh -X userid@pi-IP command
```
Wait about 2 seconds and the window for the "command" program will be displayed locally using the X/Server on the machine you sit at.  This has been a standard part of Unix for ?30-40? yrs?   If you like pain, you can even have a movie playback over this connection. For example:
```
ssh -X mypi mpv /d/D1/M/Predator.dvd.mkv
```
While it will work, it is not the best way. I'd actually play it over an NFS mount (I make NFS mounts match local mounts for media and my sanity):
```
mpv /d/D1/M/Predator.dvd.mkv
```

There's something bad about samba when compared to NFS when it comes to video streaming.  Samba routinely stutters where NFS doesn't. For other uses, performance of each is similar, unless the newest NFS is used which can easily open 20 connections to the NFS server and transfer data much faster than samba.  I only use 4 connections here.  This is part of a full NFSv4 implementation, so people buying home, commercial, NAS probably get stripped down NFS servers.

For a plex server, your new box is overkill. I use a 2015 Pentium dual core, 8G RAM, with 32TB of storage and it runs 2 VMs along with mpd, Plex and Jellyfin media servers. Jellyfin is a replacement for plex that doesn't ship our information out.  It also runs nextcloud, calibre, wallabag servers and is the NFS server for most media on the network.  Oh, and it is my OTA TV recording system too with 4 network tuners (hdhr quad).

My Pentium box, right now:
```

top - 22:36:26 **up 18 days**, 20:38,  4 users,  load average: 0.22, 0.17, 0.22
Tasks: 272 total,   2 running, 189 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  3.6 sy,  0.7 ni, 93.4 id,  0.3 wa,  0.0 hi,  0.7 si,  0.0 st
KiB Mem :  7591624 total,  **3581580 free**,  2506056 used,  1503988 buff/cache
KiB Swap:  3780604 total,  2152956 free,  1627648 used.  4759428 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND   
20323 thefu     22   2   38632   4324   3812 S   6.6  0.1   0:00.75 wget      
 1466 root     -51   0       0      0      0 S   4.0  0.0 301:36.14 irq/16-eth1
 3746 libvirt+  20   0 2637164 986.0m   3936 S   2.6 13.3   1631:09 qemu-system-x86
 2065 mpd       20   0 1319112  37540  13228 S   1.7  0.5  12:31.22 mpd       
 7048 mpd       20   0  785180  16104  12180 S   1.3  0.2   0:36.85 pulseaudio
   18 root      20   0       0      0      0 R   0.7  0.0  96:13.75 ksoftirqd/1
   30 root      25   5       0      0      0 S   0.7  0.0 236:31.16 ksmd      
20325 thefu     20   0   41916   3784   3116 R   0.7  0.0   0:00.07 top       
   10 root      20   0       0      0      0 S   0.3  0.0  84:45.03 ksoftirqd/0
  400 plex      20   0 1764228 195660   4348 S   0.3  2.6  33:53.34 Plex DLNA Server

```
Mostly idle.  A TV show is being recorded (wget) and a VM was doing something and the music server (mpd) is playing to another room. Neither Plex nor Jellyfin isn't being used.  It has been up 18 days, so a very stable system.

With plex streaming content to the projector setup, it isn't much different.
It may be a bit overkill, but I wanted to be able to transcode 5-6 streams at a time, so the cpu is rated about right for that. And this box will be my family's main file server and backup server. And I built it for just over $500, so I'm happy with it. Could I have done with less? Sure. But this way I have room to grow with it. 

And yeah I've known how to use xwindows for years, but have not used handbrake much, and really wasn't sure it would even work via xwindows. But if you say it would, great. And yes that's really the only reason I was going to put a desktop on. But honestly who cares if if it's overkill, lol, as you said my box is overkill, it van handle a desktop just fine. However I will look into using Handbrake via xwindows. And no, I don't plan on playing videos over nfs or samba lol. Not sure why you brought that up. Thanks for the help with handbrake.

---

### Post by TheFu on 2021-08-12
I don't recall whether handbrake works remotely or not.  Give me a second.
Yep, it works, though don't expect the preview to be snappy.
I know video editing tools generally don't work with any remote desktop. This is from my own attempts. They want direct access to the GPU hardware and freak out when only virtual hardware is possible - which is how all remote desktops work.

---

### Post by nate5 on 2021-08-12
I just want to use it occasionally to set up some batch video encodes. I'm not going to be doing any video editing really. Don't see how vnc is a bad solution for letting me access the desktop to run handbrake. But whatever. I got the answer I needed, I'll play around now and figure it out.

---

### Post by HermanAB on 2021-08-13
Howdy, the point is that a RPi is a small system that works best without a burdensome GUI desktop running.  

You can install a desktop system with the GUI programs you want on the RPi, then boot up to a command line only with Xorg NOT running. Using SSH, you can then run the GUI programs remotely.  SSH will forward the Xorg commands to the the local machine desktop.  The RPi will not have to do any GUI processing and will remain fast and responsive.

---

### Post by ActionParsnip on 2021-08-13
Could use handbrakecli
[https://manpages.debian.org/testing/handbrake-cli/HandBrakeCLI.1.en.html](https://manpages.debian.org/testing/handbrake-cli/HandBrakeCLI.1.en.html)

---

### Post by TheFu on 2021-08-13
> **ActionParsnip said:**
> Could use handbrakecli
[https://manpages.debian.org/testing/handbrake-cli/HandBrakeCLI.1.en.html](https://manpages.debian.org/testing/handbrake-cli/HandBrakeCLI.1.en.html)

Or ffmpeg.  I've used both.  HandbrakeCLI was a pain.  ffmpeg is what almost all these transcoding systems are based on. ALL-OF-THEM.

```
nice ffmpeg -i "$IN" -vf "scale=-2:$SCALE" "$FFMPEG_OPT" "$IN.mkv"
```
and 
```
nice ffmpeg -i "$IN" -vf "$CROP,scale=-2:$SCALE" "$FFMPEG_OPT" "$IN.mkv"
```

Are my base commands. The script around it just sets up the variables.
FFMPEG_OPT="-c:v libx264 -preset medium -crf $CF -c:a copy"

Through the files into the script and through a batch queue manager, then forget for 15 minutes ... or 5 hrs. Just depends on the size of the transcodes and the desired output quality + resolution.

---


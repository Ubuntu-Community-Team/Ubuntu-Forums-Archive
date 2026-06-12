---
title: "A few issues surrounding planning server build"
date: 2014-09-24
forum: General Help
---

### Post by joshmcc on 2014-09-24
I'm aiming to build an all-in-one file-server,torrent client,media centre using Ubuntu server and am currently in the planning stages (in terms of hardware and software). There are a few issues I've run into that I can't seem to find a solution for with any amount of googling, so thought I'd see if anyone is able to provide some helpful suggestions.

Firstly, the main requirements for the server are as follows:
> 
[LIST=1]
[*]Serve files to a variety of clients on LAN (OSX, Linux, iOS, Windows)
[*]Serve media via UPnP
[*]Bittorrent client, which is only allowed to connect to internet via VPN
[*]XBMC-based media centre
[*]Steam home-streaming (launched via XBMC)
[*]Shutdown/hibernate under a very specific set of circumstances
[/LIST]


Points 1, 2 and 3 are no issue; I have implemented these previously on an old machine and have a satisfactory system set-up. From what I've read I also assume that, given 4 is working, 5 should be straightforward (I already have a PC capable of providing the steam stream). The problems I have encountered relate to points 4 and 6, as follows:
> 
[LIST]
[*]I would like the server to be running headless most of the time to conserve resources. However, it will be connected to a TV via HDMI and I would like to be able to launch XBMC easily when required. The only input devices I plan to use with the system are an xbox 360 controller (wired, mainly/only for steam games) and a TV remote, mapped to keyboard buttons, using [flirc]("https://flirc.tv/"). Is there a way to launch XBMC directly (perhaps using a shell script) via a keyboard button or combination, from the server login prompt without first requiring a login? The scenario I envisage is:
[LIST]
[*]Switch on (already-connected) TV, and see server login prompt in terminal
[*]Press a single button on remote (possibly mapped to a button combination), and XBMC launches full-screen
[*]Exit XBMC via its own interface, and return to login prompt; switch off TV.
[/LIST]

[*]I would like the server to shut down when not 'in-use', with clients able to wake it via wake-on-lan; specifically if all of the following are true:
[LIST]
[*]Neither XBMC nor Steam are running on the server.
[*]No clients are accessing the server, either to share files (via SMB probably, for compatibility with widest range of systems), or to stream media via UPnP (miniDLNA or similar).
[*]Noone is logged in via SSH (i.e. myself, for remote admin)
[*]There are no active bittorrent **downloads** (currently using transmission-daemon but open to changing) - i.e. shutdown if there are files seeding, but not if something is still downloading
[*]It is not night-time (i.e. the server will remain on between 00:00 and 06:00, for example)
[/LIST]

[*]How much of this is possible, and how?
[/LIST]


With regard to the first issue, I am fairly clueless as to where to start.

With regard to the second issue, I am aware I can run a script at scheduled intervals using cron, and shutdown if all the required conditions are met, but checking the conditions is where I'm stuck at. I know I could check for certain static IP addresses on the LAN to see if any clients are alive, but I'd like to allow shutting down when clients are still on the network, just not accessing the server. I am relatively clueless on how to implement the rest of the requirements, despite endless googling.

I'd be incredibly grateful to anyone who is able to help me with this, and will probably post a guide once everything is done, in the hope that the information might be of use to others.

---

### Post by TheFu on 2014-09-24
Use Samba for Windows file server.
Use NFS for OSX and Linux file server.
Install Plex Server for all media serving - this is DLNA and works with any DLNA client or renderer - xbmc, chromecast, smart-tvs and networked bluray.

I don't know anything about iOS - unless you are talking Cicso iOS - which I doubt.

XMBC should be started up always - use PLEXBMC plugin to access the plex served files. Do NOT let XMBC manage the files, trust me.  I did it that way for a few years and wish I'd switched to Plex earlier.  No need for any Plex online accounts either. NONE.  I don't have one, don't use it and streaming anywhere on the home LAN works.

I don't know anything about steam - sorry.

I don't know anything about bittorrent either - sorry.

Turning off (hibernate/standby) for a file server is a **terrible idea**.  Use a 16W CPU if low power use is what you want. With a few spinning HDDs, that's still just 26W of power while actively running.  Standby and hibernate don't always work so well with HDMI connections. For a time, standby would remove audio drivers, but not load them back up on resume.  Just sayin'.  This is all extremely specific for every different motherboard, every different APU/GPU combination, every different HDMI chipset.

Don't forget that lower power use usually means less noise - that is important for a media center.

My system is fabulous, but you can't buy the same anymore. It hasn't been available for years.

---

### Post by joshmcc on 2014-09-25
Thanks for the advice. 

Would you mind elaborating on a couple of those points please?

What is so terrible about letting XBMC manage files? I've been doing it for a while and had no problems so far. 
Also, why would I want XBMC running all the time? I only need it running when I want to watch it via the TV, and presumably the system would run marginally faster elsewhere/lower power if XBMC wasn't running constantly? 

Also, what exactly would be the issue with having a file server shut down most of the time and only boot up when needed? The vast majority of the daytime I won't be using it and it seems like a huge waste of power to keep it running when not needed.

---

### Post by TheFu on 2014-09-25
> **joshmcc said:**
> Thanks for the advice. 
Would you mind elaborating on a couple of those points please?
Sure. There are 100 different ways to solve each f the issues, these are only the way my experience (20+ yrs) lead me.

> **joshmcc said:**
> What is so terrible about letting XBMC manage files? I've been doing it for a while and had no problems so far

Let Plex do it. It is centralized then. Since Plex began life as an XBMC fork, you already have the directory structures needed for movies and TV.  It is easy go get confused when 2 pieces of software appear to be managing the same directory structure.  Think of XBMC as "playback only" and think of plex as the DB manager and for streaming.  Having duplicate management is more of a waste.  Use plex, you'll thank me .... or not.

> **joshmcc said:**
> . Also, why would I want XBMC running all the time? I only need it running when I want to watch it via the TV, and presumably the system would run marginally faster elsewhere/lower power if XBMC wasn't running constantly? 

If the screen isn't on, how will you know the difference?  From a usability perspective, turning on the TV and having that XMBC screen already there is key.  [Critical for W-A-F]("https://en.wikipedia.org/wiki/Wife_acceptance_factor").  For me, that is worth the $5/yr in electrical costs.  XMBC isn't a huge CPU suck, about 9% here when idle. 108% during playback of GPU-handled video.

Of course, if this machine is an 8 core AMD monster sucking 165W just for the CPU, this cost will be much higher.  My Plex/XBMC/NFS server is an AMD E350 and uses 26W while doing everything it can. It is on 24/7 with the storage part as the center of the network storage for about 5 other systems.  Those other system expect the storage to be available.  I don't use it for backups - it is primary storage, but it could be used for automatic backup storage.

> **joshmcc said:**
> Also, what exactly would be the issue with having a file server shut down most of the time and only boot up when needed? The vast majority of the daytime I won't be using it and it seems like a huge waste of power to keep it running when not needed.

A file server that isn't already on when you need it becomes a hassle. Having to turn it on and off is also a hassle.  It is also difficult to mount the storage to other systems.  Those other systems want/need that storage to be available. If it isn't, depending on the mount options, they could lock up.  Now, instead of just using the storage, it will become a pain - turning on 2 systems to use 1?  

Standby sometimes works fine, but often it doesn't work at all, especially with HDMI connections involved. If I were able to get that working, perhaps a different solution would be used.  Between the audio not coming out of standby and the video being screwed, and the remote control not being able to wake the system ... it is just easier to leave it on.  OTOH, if you expect all these things to easily work and they do not, it is best to have a backup plan.

But .... it is your system. Do what you like and learn these things for yourself.  Perhaps you can do better than I. I wish you well and I'll be jealous if you do get farther than I have.

---


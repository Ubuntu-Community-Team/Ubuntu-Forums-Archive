---
title: "Windows 8.1 dropping Samba connection"
date: 2015-07-17
forum: General Help
---

### Post by Cyphie on 2015-07-17
So I'm running into some problems with Samba and my Windows 8.1 machine. I did manage to find a way that makes it manageable but it is far from perfect.
The problem I'm having is that the Windows 8.1 machine seems to drop the network connection after being inactive for a while, at that point I can still connect to the laptop without any problems through RDP etc. 
I made sure that the network adapter does not get turned off or anything to save power and the machine doesn't go in standby mode or anything.

After forcing the machine manually to connect to the network share again it starts working again. So under normal use this wouldn't be that much of a problem. Were it not that it is running a media server and the media files are located on the Ubuntu machine with the Samba shares.
So if it drops he connection I can not stream any media anymore without starting a RDP session and reconnecting the network share.

So I did find a temporarily solution that seems to stop the disconnects. I made a bat file on the Windows machine that writes to a .txt file every 5 seconds. Haven't had problems for the last couple of hours while it usually occurs every time I am inactive for a while and want to watch a tv series or a movie or something. That leads me to think that there is some kind of time-out going on that is causing this problem but I have no idea what I can do to solve this.

I already tried adding the following line in smb.conf
```
keepalive = 300
```

That one doesn't seem to be the solution. Was hoping someone here could help me with this problem.
Tried to Google the issue but I came up with nothing that helped so far. I realize it is probably not a issue with Ubuntu itself but I thought you guys would probably be more experienced with this then I am.

---


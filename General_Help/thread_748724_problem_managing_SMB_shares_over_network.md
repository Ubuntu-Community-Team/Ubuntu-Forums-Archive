---
title: "problem managing SMB shares over network"
date: 2008-04-07
forum: General Help
---

### Post by ac251404 on 2008-04-07
I wasn't sure of the proper forum for this so I just put it here. 

I just setup a brand new box with Ubuntu Gutsy 7.10 as a file/general server and media center. I also have torrentflux installed for downloading torrents. The problem is, I would like to be able to move files around on the server from my desktop, and it works, but is very slow. If I use VNC to connect to the server and move a video file it takes about 20 seconds. If I try and move the same file to the same location over SMB it takes >2 minutes. My first guess is that it is for some reason transferring the file to my desktop then back to the new location on the server (even tho this is very silly). I'm not sure if thats the case or not, but it seems to fit the problem. Can anyone confirm this behavior for Nautilus and SMB shares? Is there some way I can prevent this from happening so I don't need to VNC into the server all the time to manage my downloaded files?

thanks
-ac

---


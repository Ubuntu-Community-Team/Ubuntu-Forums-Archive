---
title: "Clamav local server issue"
date: 2013-09-19
forum: General Help
---

### Post by deevakarpk on 2013-09-19
[COLOR=#500050][FONT=arial]Hi Support,[/FONT][/COLOR]
[COLOR=#500050][FONT=arial]

We have setup a local clamav server for our organization and all our clients were connected to it to seek updates from our local server. 


Now our client machines are not fetching updates from our local server and it ends up with the below error message when I try to do a manual update using freshclam. 

Also when I run freshclam in our local server, the main.cvd file got deleted and only main.cld file exists in the server. May I know the difference between these two files?


==============================
Wed Sep 18 10:26:21 2013 -> freshclam daemon 0.97.8 (OS: linux-gnu, ARCH: x86_64, CPU: x86_64)
Wed Sep 18 10:26:21 2013 -> ClamAV update process started at Wed Sep 18 10:26:21 2013
Wed Sep 18 10:26:22 2013 -> WARNING: getpatch: Can't download main-55.cdiff from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:22 2013 -> WARNING: getpatch: Can't download main-55.cdiff from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:22 2013 -> WARNING: getpatch: Can't download main-55.cdiff from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:22 2013 -> WARNING: getpatch: Can't download main-55.cdiff from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:22 2013 -> WARNING: getpatch: Can't download main-55.cdiff from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:22 2013 -> WARNING: Incremental update failed, trying to download main.cvd
Wed Sep 18 10:26:23 2013 -> WARNING: getfile: main.cvd not found on remote server (IP: xx.xx.xx.xx)
Wed Sep 18 10:26:23 2013 -> WARNING: Can't download main.cvd from [clam.xx.com]("http://clam.xx.com/")
Wed Sep 18 10:26:23 2013 -> Trying again in 5 secs...
Wed Sep 18 10:26:26 2013 -> 
==============================


May I know why this happens and what is the resolution for this? 

Thanks in advance.

Deevakar 


[/FONT][/COLOR]

---

### Post by Kirboosy on 2013-09-19
Welcome to the forums! :D

There is [documentation]("http://wiki.contribs.org/Clamav:freshclam_update#The_howTO") on recreating your virus databases. .cld is created from last .cvd + .cdiff, or last .cld + .cdiff. 

You may wanna try to set the master freshclam to use ScriptedUpdates off, then it will always fetch a .cvd

Hope that helps!
~Caboose

---


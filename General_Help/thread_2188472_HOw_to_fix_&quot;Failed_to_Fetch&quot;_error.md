---
title: "HOw to fix &quot;Failed to Fetch&quot; error"
date: 2013-11-17
forum: General Help
---

### Post by suomalainen on 2013-11-17
Ubunteros,

I need help fixinf these errors below. not sure how to do it.

Your help appreciated.

Thanks

Failed to fetch [http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_30.0.1599.114-1_i386.deb](http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_30.0.1599.114-1_i386.deb) 404  Not Found [IP: 80.239.229.218 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libav-tools_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libav-tools_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libpostproc52_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libpostproc52_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavfilter2_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavfilter2_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libswscale2_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libswscale2_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavdevice53_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavdevice53_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.8-0ubuntu0.12.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.8-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_4.8.3.0-1_i386.deb](http://dl.google.com/linux/talkplugin/deb/pool/main/g/google-talkplugin/google-talkplugin_4.8.3.0-1_i386.deb) 404  Not Found [IP: 80.239.229.218 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/ffmpeg_0.8.8-0ubuntu0.12.04.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liba/libav/ffmpeg_0.8.8-0ubuntu0.12.04.1_all.deb) 404  Not Found [IP: 91.189.91.15 80]

---

### Post by ian-weisser on 2013-11-17
http's "404 Not Found" means the same thing regardless of the application you are using. See [http://en.wikipedia.org/wiki/HTTP_404](http://en.wikipedia.org/wiki/HTTP_404)

Wait a few minutes and try again.
If it has *always* failed, do mention so.

---

### Post by suomalainen on 2013-11-18
I think it's a little more then that because this problem is ocurring during update. If critical updates cannot be downloaded the new source needs to be pointed to.

Thus I need to know how to point to new source.

---

### Post by Bashing-om on 2013-11-18
suomalainen; Hi !

The mirror appears to be up at this time:
> 
sysop@1304mini:~$ ping -c 3 91.189.91.15
PING 91.189.91.15 (91.189.91.15) 56(84) bytes of data.
64 bytes from 91.189.91.15: icmp_req=1 ttl=48 time=66.1 ms
64 bytes from 91.189.91.15: icmp_req=2 ttl=48 time=60.8 ms
64 bytes from 91.189.91.15: icmp_req=3 ttl=48 time=64.3 ms

--- 91.189.91.15 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 60.832/63.762/66.105/2.192 ms
sysop@1304mini:~$ 


And to change to a faster/closer/different mirror:
> 
SOFTWARE SOURCES
On the Ubuntu Software tab, select the drop down for "Download From"
Select Other
Choose your country then click on "Choose best server"....This will ping all the mirror sites for the best ping and then it will select the better server.
And once done, update from the Software Center.


[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by suomalainen on 2013-11-18
Now I got this error message during updates............

W:Failed to fetch [http://repo.mate-desktop.org/dists/precise/main/source/Sources](http://repo.mate-desktop.org/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://repo.mate-desktop.org/dists/precise/main/binary-i386/Packages](http://repo.mate-desktop.org/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ian-weisser on 2013-11-18
Well, repo.mate-desktop.org does return 404. The server exists, but the URL does not exist.
Have you checked if the mate.org project has any announcements about it? It's their server, not Ubuntu's, and they support mate.

Has the link *ever* worked recently? Looks like it's missing an element:
```
doesn't work: http://repo.mate-desktop.org/dists/precise/main/source/Sources
works:        http://repo.mate-desktop.org/ubuntu/dists/precise/main/source/Sources
```
So you should edit that URL in your /etc/apt/sources.list or /etc/apt/sources.list.d file.

---

### Post by suomalainen on 2013-11-21
HI,

I went into Synaptic Package manger --> Repositories -->Other Software and tried to add:

[http://repo.mate-desktop.org/ubuntu/dists/precise/main/source/Sources](http://repo.mate-desktop.org/ubuntu/dists/precise/main/source/Sources)

in the apt LINE but the "add source" button remains grayed out.

Can't figute this one out.

---

### Post by suomalainen on 2013-11-21
HI Again,

I went into Other Software and deleted anything with MATE in it.

Then with terminal I did:

sudo add-apt-repository "deb [http://repo.mate-desktop.org/ubuntu](http://repo.mate-desktop.org/ubuntu) precise main"
sudo apt-get update

Went back into Other Software to see if changes took effect and they did.

Opened Synaptic and did an update. Issue did not present itself.

Result. Problem solved.

Thanks everyone for your help!

---


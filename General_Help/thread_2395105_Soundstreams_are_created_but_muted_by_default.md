---
title: "Soundstreams are created but muted by default"
date: 2018-06-26
forum: General Help
---

### Post by johannes97 on 2018-06-26
Hello dear community,
since my search for a solution failed and many of my solutions are out of this forum, I'd like to ask you for your help today.

I've encountered this problem the first time with Spotify.
The software opens a playback-stream but on creation it is muted.
Also if a new stream gets created alongside the already existing and manually unmuted stream of the software, the unmuted stream of the software will get muted again
Later today I noticed that the videoplayer parole and VLC are also affected.
Firefox and Teamspeak3 are not affected at all.

If you need more information feel free to ask for it.
Thank you in advance.

[URL="http://i.imgur.com/4eYgQpV.png"]
  [IMG]http://imgur.com/4eYgQpVl.png[/IMG]
[/URL]

---

### Post by johannes97 on 2018-07-04
*bump

---

### Post by johannes97 on 2018-07-08
Xubuntu-IRC has solved the problem.
For anyone having the same issues
```
sudo nano /etc/pulse/default.pa
```
and then find the following line
```
load-module module-role-cork
```

edit it to look like this 
```
#load-module module-role-cork
```

---


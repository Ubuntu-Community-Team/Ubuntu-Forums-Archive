---
title: "tor transparent to youtube"
date: 2018-09-10
forum: General Help
---

### Post by JamButty on 2018-09-10
I would think this has been addressed, but I did not find it in searching. Recently, I watched a youtube video while on Tor. The next day I booted up, when into standard Firefox on a different operating system and pointed to youtube. There, among the recommended video selections on the youtube homepage was the video I had watched the day before from within Tor. Nothing embarrassing about the video, but it was not a popular video and could not possibly have been thrown up by youtube as a recommendation based on general popularity, nor history ostensibly as I was not even on the same operating system (a rare trip to windows). Yet there it was. So clearly, TOR is transparent to Youtube, which can still ID a user, hold the data at host (there was no local cookie), then used that data for that ID the next time it invokes Youtube. This is very strange.
Does anyone have experience with this?

---

### Post by TheFu on 2018-09-11
If you login to any accounts between both systems, expect to be tracked. 

Also, the Tor browser had a zero-day bug announced last week. Read that it was something to do with bypassing NoScript.  Being anonymous on the internet isn't easy.

---

### Post by JamButty on 2018-09-12
no login to youtube or anywhere, no. Since the link persists across Ubuntu and Windows systems on the same physical device, I have to assume a cookie or similar is held at the youtube host marked by IP. That is not so surprising, but getting my IP through TOR is.

---

### Post by TheFu on 2018-09-12
Is the OS running from read-only media?  If you allow html5 local objects, that could help tracking. 

Also the EFF has a way to figure out how unique your browser seems in the world.  [https://panopticlick.eff.org/](https://panopticlick.eff.org/)

Being anonymous on the internet is hard.

---

### Post by JamButty on 2018-09-12
not read-only media. I assume the video was in HTML5. I had the impression youtube has been converting all videos submitted to it to html5 for a while now. Tor was on the lowest security level.

---

### Post by TheFu on 2018-09-12
I would try it with read-only media for the OS and reboot between attempts.
I would also disable javascript, except for the exact domains required. For youtube, I think that is 3.

Specifically for youtube, I find it easier to use a VPN with youtube-dl instead, but we cannot talk about that here.

---

### Post by JamButty on 2018-09-12
thanks!

---


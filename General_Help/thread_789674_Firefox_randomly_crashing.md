---
title: "Firefox randomly crashing"
date: 2008-05-10
forum: General Help
---

### Post by Midnightsun on 2008-05-10
Hey guys,

Ever since I installed Ubuntu I've had a problem with firefox crashing at random intervals.  Initially I thought it was flash video causing the problem, as this seemed to be when it was happening, but it's just happened while browsing ubuntuforums which is a fairly innocuous site (in terms of plugin requirements) for the most part and certainly no flash video.

Firefox can just be restarted and pages reloaded, so it's not the end of the world, however it seems to be happening with increasing regularity.  Is there anyway to troubleshoot this problem?  I've no idea what's even causing it...

Edit: (btw - using Hardy)

---

### Post by Midnightsun on 2008-05-15
Sorry to bump this guys, but still having the same issues with Firefox just randomly crashing.  It generally seems to be caused by flash video, but not always.

Should I just uninstall all the firefox packages and start afresh?  Is there any way I can actually trouble shoot this and find out what's causing the crashes?

---

### Post by mike555 on 2008-05-15
If you have ad-ons you could try disabling a few at a time to see if that helps, or you could try Flash 10 beta (that helped me)......

---

### Post by kk0sse54 on 2008-05-15
It happens to me too especially when on youtube it just loves to crash. Partly because firefox 3 is still beta and is very unstable with flash videos. You could try flash 10 beta it might work but for me I tried it and it did nothing for me. Another thing you can do is downgrade to firefox 2. In the tutorial section of the forums I think there are a few how-to's on how to do that because you are not the only one experiencing problems

---

### Post by iaswni on 2008-05-16
Well, i had the same problem when watching videos. 
What i did was

 *sudo apt-get remove libflashsupport*

and solved my problem.

For more details go [_here_]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")

---

### Post by geovino on 2008-05-16
> **iaswni said:**
> Well, i had the same problem when watching videos. 
What i did was

 *sudo apt-get remove libflashsupport*

and solved my problem.

For more details go [_here_]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")

I tried that... FF crashed just the same as before. I'm using Opera until the new Flash comes out.

---


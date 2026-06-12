---
title: "Help - Went on hols &amp; my machine wont boot up?"
date: 2007-09-22
forum: General Help
---

### Post by LadyFox on 2007-09-22
Hi there, 

I hope that some kind soul can help me. 

I have returned from a 2 week vacation today to find that my Ubuntu machine has died.  My previous posts are [here]("http://ubuntuforums.org/search.php?searchid=27561232") but essentially its an old Dell Dimension box that has been running Ubuntu very happily since my last posts.  My partner swiched my machine off before we left home, i turn it on today and it doesnt come on.  

I have twin monitors running from a NVidia card that i installed a while back though it seems this change has been lost as the only way i can access the machine is to plug a monitor into the onboard VGA, and in that case it boots straight into X server.  I dont get what has gone wrong here. 

Can anyone assist me with getting my machine back up and running?  I went through a lengthy xorg.conf edit ages ago and really dont want to do it again, is there a command i can enter in terminal  to get the last known good config?  I have data on the HD that i really dont want to lose.

---

### Post by john.nicholls on 2007-09-22
As yiu know, the configuration file is /etc/X11/xorg.conf. If a backup was created, it should be named /etc/X11/xorg.conf~. You can read the files with cat.

---


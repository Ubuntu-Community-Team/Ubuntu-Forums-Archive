---
title: "[SOLVED] Apache2 troubles"
date: 2008-06-04
forum: General Help
---

### Post by Aquaman420 on 2008-06-04
I set up my apache server and downloaded the noip2 update client and everything was working fine for about 3 week then all of a sudden I can no longer access my server the message that is displayed states that the server took to0 long to respond.  I am not too great or knowledgable with servers or computers for that matter.  When I type in the [http://localhost](http://localhost) address I can see my index.html file but not when I type in my domain address, not sure if that helps in figuring out the problem.  Any ideas are always appreciated


Thanks for the response cheater but unfortunately my problem is that sometimes I am just plain stupid.  I got a Wii, hooked it up, my network address changed so no port forwarding for me.  Changed my router settings it's all good.  Solved.

---

### Post by nhandler on 2008-06-05
Well, based on your explanation of the problem, it sounds like Apache2 is running just fine. The issue is probably with noip2. If you know your computers public IP address, try connecting to that. If it works, it means noip2 is pointing to the wrong IP. You can manually modify this by going to [http://www.no-ip.com/](http://www.no-ip.com/) or running 'noip2 -C' to recreate the configuration file.

---


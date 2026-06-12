---
title: "Remote execution of programs?"
date: 2006-09-10
forum: General Help
---

### Post by Mastus on 2006-09-10
Hi.

I have two computers (main computer and a server), and I have a lot of video encoding tasks at hand, so I'd like to know if there's a possibility to execute encoding tasks on server (=steal the processor power)?

VNC would be the answer, but the server doesn't have X Window System, or any of the video encoders installed. 

Clustering would be the answer, but from what I have read, the setup is tedious... and the server is 64-bit and the main one is 32-bit...

So is there a solution where you can "Say to the other computer, that do this task for me?"

---

### Post by kidders on 2006-09-10
Depends on how complex/efficient you want your setup to be. The bitness of your computers doesn't make a whole lot of difference ... 64-bit machines are quite happy to emulate 32-bit operation.

I would recommend against using VNC or other complex graphical environments, because they waste CPU cycles you could be using for the tasks you want to perform.

The easiest option might be to install enough software on your server to let it perform your video encoding itself, and use SSH to tell it to do things. Too basic?

**Edit:** Since you used the word "server" to describe one of your machines, don't forget to nice any encoding operations you ask it to do pretty ruthlessly!

---


---
title: "Multi user Blender server"
date: 2015-11-16
forum: General Help
---

### Post by mcarrara2 on 2015-11-16
I work at a school and have an idea that I want to try.  I teach a beginning tech class where we look at different computer applications.  Next unit is on 3d drawing and animation.  I wanted to use Blender as the software.  However I can't get access to any computers powerful enough to run it.  I do have access to Chromebooks.  Here is my idea:
1. Spin up a GPU instance on AWS with Nvidia Grid GPU.  
2. Install Ubuntu desktop(?) and blender.  
3. Now i want to connect 8 students to the server, each with their own session and desktop.  I looked at VNC, but it looks difficult to have 8 different connections at the same time.
4. I am thinking of XRDP, but I am concerned because Microsoft's RDP does not use the 3d acceleration from the GPU and I'm not sure XRDP will.
5. Chromebooks have  both an RDP and VNC client so either will work.
6. I can't afford to spin up an AWS instance for each student.

Questions:
1. Am I completely crazy and my idea will not work?
2. Is XRDP the way to go or VNC?

Thanks

Mark

---


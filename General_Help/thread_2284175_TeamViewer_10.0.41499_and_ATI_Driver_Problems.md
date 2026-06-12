---
title: "TeamViewer 10.0.41499 and ATI Driver Problems"
date: 2015-06-27
forum: General Help
---

### Post by The_Avenger on 2015-06-27
I installed a new Ubuntu 14.04 TLS and TeamViewer 10.0.41499. It worked just fine.

I then updated the video drivers for my ATI HD 7950 with the proprietary ATI drivers. Since then I get the following behavior from TeamViewer:
- While on the login screen, I can connect and type
- Once logged in I see the screen but whatever I do (e.g. start an application) the screen is not updated. However the action happens, i.e. when I look at the physical monitor the application has run
- If I change the monitor in TeamViewer (I have 4 monitors on the machine) and go back to the initial one, I see the updated picture. Any further changes are again not visible

I tried restarting the machine multiple times, removing and reinstalling TeamViewer but there is no change. I am connecting to it from a Windows 8 machine running TeamViewer 10.0.43879, the newest available version for Windows.

Any ideas what might be causing the problem or where to look for it?

---

### Post by The_Avenger on 2015-06-27
I found the solution here: [http://ubuntuforums.org/showthread.php?t=2088710](http://ubuntuforums.org/showthread.php?t=2088710)

The quality of the connection has to be changed on the client. In TeamViewer 10 the configuration is either under Extras -> Options -> Remote control -> Quality (for all connections) or in the computer connection properties under Advanced -> Quality. The only option that seems to work is Custom, it won't work with any other (Optimize speed, Optimize quality or Automtic)

---


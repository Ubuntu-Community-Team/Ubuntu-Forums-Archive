---
title: "Weird problem with dualhead setup"
date: 2008-01-01
forum: General Help
---

### Post by niviq on 2008-01-01
I have problems setting up dualhead on Kubuntu. The weird thing about this is that there is nothing wrong if i use xinit to start xserver. I can then launch kdesktop, kwin, kicker and so on, except for kdeinit which does nothing (so klauncher won't run either.) The loginscreen is also set up correctly with to screens.

However if i use startx or the login-screen to start KDE, the conditions are as follows:
1. The second screen stops refreshing the background and kdesktop is not on it.
2. You can move windows partially in onto the second screen but not drag it over (like when xinerama is missing, or something.)
3. Ksnapshot takes screenshot of only the first screen. Whilst when running by xinit it grabs the whole desktop like it should.

This makes me belive that kdeinit is at blame, as the problem occurs at login..

Please help me troubleshoot this :confused:

If you are interested in my xorg.conf -file, then it's here: [http://pastebin.com/m329e72fa](http://pastebin.com/m329e72fa)

---


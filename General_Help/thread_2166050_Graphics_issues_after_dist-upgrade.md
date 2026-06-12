---
title: "Graphics issues after dist-upgrade"
date: 2013-08-07
forum: General Help
---

### Post by jeliocranch on 2013-08-07
I've had an issue with my graphics after running ```
apt-get update && apt-get dist-upgrade
``` a few weeks ago.
Seems after about 5-10 minutes, the screen goes black and tries to go to sleep, regardless of whether or not the machine is being used.  Upon waking, the graphics are scrambled though the mouse pointer is clear and responsive.
I've disabled any power-saving features of the screen, never letting it power-down, nor dim or go to screen saver, but it hasn't helped.

Ctrl+Alt+F2 (3,4,etc) can open a clean shell.  ```
startx
``` returns something like X is running, and Ctrl+Alt+F7 returns to scrambled graphics.

I'm running 13.04, kernel 3.8.0-27.  Open source default driver w/ Radeon HD 6850 card.  I did have fglrx-updates enabled for a while, but it would crash Skype (or vice versa), so I went back to OS driver.

My workaround has been to open an arbitrary window from Settings.  Any settings window works to stop the screen power-off and resulting scramble, as long as the window stays open.

Some posts from 2010 seem somewhat related, but they seem related to very specific hardware.

Any help would be greatly appreciated

---

### Post by sudodus on 2013-08-07
Have you tried if 12.04 LTS has more stable graphics with your Radeon card? It might be the solution for you. Another solution might be to go back to the previous kernel (from before the dist-upgrade).

---

### Post by jeliocranch on 2013-08-08
While I never saw this problem with 12.04, I hadn't seen it in 13.04 either until now.  I have not tried reverting to a prior kernel, but I have a sneaking suspicion it relates to either my temporary installation of fglrx-updates, or the power-management (because when the settings window is open I believe it disables power-management).

Oddly, I closed the settings window yesterday and had no issues, and several subsequent updates have done kernel work.

---

### Post by sudodus on 2013-08-08
Well, come back here, if the problem pops up again! Maybe some people with the same or similar graphics cards will see your thread and help.

---


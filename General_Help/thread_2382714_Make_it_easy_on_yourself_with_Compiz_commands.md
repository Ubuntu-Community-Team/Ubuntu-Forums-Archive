---
title: "Make it easy on yourself with Compiz commands"
date: 2018-01-16
forum: General Help
---

### Post by Cavsfan on 2018-01-16
Lets say you use Cairo Dock and put the computer to sleep (suspend mode), come back a few hours later, wake the computer up and Cairo Dock looks a little messed up.
Here is an easy way to fix that. Open up Compiz Config Settings Manager (CCSM) and at the top left Commands under General enable that:
[[IMG]http://en.zimagez.com/miniature/screenshot12018-01-1616-03-49.png[/IMG]]("http://en.zimagez.com/zimage/screenshot12018-01-1616-03-49.php")

Using the top counting as F12, I put at F10, or Command Line 2 commands to kill Cairo Dock, sleep for 5 seconds and then restart Cairo Dock (killall cairo-dock && sleep 5 && cairo-dock -o).
[[IMG]http://en.zimagez.com/miniature/screenshot22018-01-1616-07-51.png[/IMG]]("http://en.zimagez.com/zimage/screenshot22018-01-1616-07-51.php")

Then when you click on the Disabled box by Run Command 2, which corresponds to what we have already setup, if will ask you to set the keys up.
Simultaneously touch **control** + **shift** + **F10** then press OK.
[[img]http://www.zimagez.com/miniature/screenshot32018-01-1616-08-18.png[/img]](http://www.zimagez.com/zimage/screenshot32018-01-1616-08-18.php)

Then in the future when you want to restart Cairo Dock, just press Cntl+Shift+F10 and viola.
This can be done to simplify a lot of things like restarting conkys or anything else.

---


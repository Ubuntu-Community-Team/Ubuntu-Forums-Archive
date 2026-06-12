---
title: "Ubuntu Sluggish and Launcher/Menu Bar Disappeared after Nvidia Driver Update"
date: 2012-11-03
forum: General Help
---

### Post by Dal18 on 2012-11-03
I just recently started using Ubuntu (12.04) since a few weeks ago and noticed that the interface is very slow and sluggish:  
[LIST]
[*]On Dash, I have to type the entire app name and wait a few  seconds before it shows up in the search box, and a bit later before it  displays search result
[*]Opening new files or applications takes also quite long and awkward
[*]Dragging icons or moving app windows around is not very  spontaneous too: I have to take extra attention in moving the mouse  otherwise Ubuntu would not do a correct movement or might ends up doing  something incorrect instead e.g. opening the windows to full screen  options or move the file to different folders, which is frustrating
[/LIST]
  My PC is a few years old already (1.7 GB RAM) so this could be a  reason too but when I checked in System Monitor it's hardly ever  consuming much memory. Plus web-surfing on Firefox is actually lightning  fast (much more than Windows), so I suspect there might be something  wrong with the graphics driver (mine is GeForce 7050).


  I checked around System Settings and found an option to update the Nvidia driver. So I tried it and restarted, as instructed. 



  Now, I got into a big problem upon restart... as the login-screen  windows (where I have to type in the password) would take several  attempts to display and finally did not manage to (it'd freeze for  several seconds before there's any movement again). The background  screen also kept reloading several times too and at some point the  screen turned black with pixelated color strips running on the bottom  1/3 of the screen, and after a long while the background screen would  come up again. Eventually I'd manage to be able to access the desktop  but the launcher, top menu bar and app windows border would all  disappear.


  I searched around and found many other people have this similar  problem after updating Nvidia driver too, and on some threads the  suggestion is to use "killall -u $USER" in command line (it's the only  thing among various online suggestions I could do, as at that point I  could not access Terminal without the launcher - Ctrl-Alt-T doesn't work  for me). So I did that and was able to access the desktop correctly  again with launchee/menu by creating a new account. But I would still  have the same problem if logging into my original account.
  So I just finally tried upgrading to 12.10 and now can access my  original account with fully-functional desktop - the launcher, menu and  windows border are all back now.


  However, the problem with sluggishness still remains. And now I get scared of ever having to update the Nvidia driver again!


  I wonder if anyone knows what's the reason that updating the Nvidia  driver is causing this problem and is there a way I can update it safely  in the future? I'm still not sure how to solve the problem with the  sluggishness too and not sure where else to look to find a solution.

---

### Post by hal8000 on 2012-11-03
I've never had that problem on any linux distribution.
What I would do is install htop (terminal based resource monitor)

```
sudo apt-get install htop
```


Start htop from your terminal, increase the size of terminal window if needed and note CPU usage. It may give a clue as to what process is consuming most resources.

---

### Post by Dal18 on 2012-11-05
Thanks, I did that and it shows the CPU usage is about 5% when inactive, and about 30% when I'm surfing the web. Memory usage is about 800 out of 1,763 MB.

htop shows it's mainly Firefox that's consuming the resources (it's displayed on several lines however - about 30), followed by Compiz.

---


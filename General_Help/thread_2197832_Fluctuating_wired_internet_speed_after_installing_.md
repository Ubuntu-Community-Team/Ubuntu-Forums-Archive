---
title: "Fluctuating wired internet speed after installing Ubuntu 13.10"
date: 2014-01-05
forum: General Help
---

### Post by zach617 on 2014-01-05
Switched from winxp and had speed of bout 600-700kbs but now its wilding going from 60kbs all the way up to 900kbs, speeds ive never had before, but mostly staying at around 60kbs I have no idea what to do, im really new to LInux. I used the automatic updater and updated all of my files but I dont know what else to do.

Also it seems to strangely jump in speed massively when I click on the 'Wired connection 1' in the top right of the screen but then it goes back down to 60kbs

Also it only seems like my download speed is affected, when Im browsing the web its lightning fast.

---

### Post by varunendra on 2014-01-06
Welcome to the forums zach617 !

May we see which card and driver you are using? To give us that info, please open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo lshw -numeric -C network
```
..and post back its output in your next post.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---


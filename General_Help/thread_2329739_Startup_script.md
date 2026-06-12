---
title: "Startup script :?"
date: 2016-07-04
forum: General Help
---

### Post by Furycd001 on 2016-07-04
HI Guys.

I use a terminal command to set a chosen video as my desktop wallpaper. I have three videos which I want to run one after the other (when one finishes the second one starts etc) upon booting into my desktop. Anyway I have added the three commands into my /etc/rc.local file but they do not run whenver the desktop first boots. Below is the command I use to run and edit the rc.local file. Also is a link to the rc.local file itself. Many thanks in advance for your help.

sudo pluma /etc/rc.local

[http://paste.ubuntu.com/18474390/](http://paste.ubuntu.com/18474390/)

---

### Post by Skaperen on 2016-07-04
have the scripts run the *env* command with output to a specific file, like:

in the 1st script:

> env > env-1.out

then look at these files and tell us what **DISPLAY** is.

---

### Post by CantankRus on 2016-07-05
Is /etc/rc.local the right place to put this?
Won't it try to run before you are at a graphical desktop and fail?

Why not just place the path to a script in startup applications?
eg 
_vlc-wallpaper.sh_
```
#!/bin/bash

cvlc **--play-and-exit** --video-wallpaper --no-audio '/home/furycd001/Downloads/mex' '/home/furycd001/Downloads/mex1.mp4' '/home/furycd001/Downloads/mex2.mp4'
```
[ATTACH=CONFIG]269969[/ATTACH]

I tried your script and it does not get past the first instance of cvlc without the **--play-and-exit** option.
You can also just use the one command as above.

PS: The first vid is '/home/furycd001/Downloads/**mex**'  ....is that supposed to be '/home/furycd001/Downloads/**mex.mp4**'

---

### Post by Furycd001 on 2016-07-05
> **Skaperen said:**
> have the scripts run the *env* command with output to a specific file, like:

in the 1st script:



then look at these files and tell us what **DISPLAY** is.

Here's what that command output >> [http://paste.ubuntu.com/18580385/](http://paste.ubuntu.com/18580385/) << Display is set to 0.

> **CantankRus said:**
> Is /etc/rc.local the right place to put this?
Won't it try to run before you are at a graphical desktop and fail?

Why not just place the path to a script in startup applications?
eg 
_vlc-wallpaper.sh_
```
#!/bin/bash

cvlc **--play-and-exit** --video-wallpaper --no-audio '/home/furycd001/Downloads/mex' '/home/furycd001/Downloads/mex1.mp4' '/home/furycd001/Downloads/mex2.mp4'
```
[ATTACH=CONFIG]269969[/ATTACH]

I tried your script and it does not get past the first instance of cvlc without the **--play-and-exit** option.
You can also just use the one command as above.

PS: The first vid is '/home/furycd001/Downloads/**mex**'  ....is that supposed to be '/home/furycd001/Downloads/**mex.mp4**'

I made the wallpaperbg.sh file with the code above and saved it to my home folder. I then made the file executable and added it to my startup applications list. I logged out and back in only to find that it has partially worked. While yes the video loads automatically and starts playing now, it does not load as the background. It opens up and loads inside the actual vlc application (full window title, close/minimise buttons & vlc controls etc) with my normal background loading as always. Thank you very much for your suggestion, but do you have any more ??

---

### Post by CantankRus on 2016-07-05
Did you use **cvlc** and not vlc
It works here when I test with a video.
Just run the cvlc line in a terminal and see if it works.

---

### Post by Furycd001 on 2016-07-06
> **CantankRus said:**
> Did you use **cvlc** and not vlc
It works here when I test with a video.
Just run the cvlc line in a terminal and see if it works.

If I type the command into terminal it runs perfectly fine setting the video as wallpaper. If I put the command or sh file in my start-up list it just simply loads the video in vlc itself and not as a background.

---

### Post by CantankRus on 2016-07-06
Also test the script by pasting into a terminal the same path used in startup applications.
You could also try delaying the start of cvlc by adding a sleep line to the script.
eg
```
#!/bin/bash

**sleep 5**
cvlc --play-and-exit --video-wallpaper --no-audio '/home/furycd001/Downloads/mex' '/home/furycd001/Downloads/mex1.mp4' '/home/furycd001/Downloads/mex2.mp4'
```
If that doesn't work try **sleep 30**.

Can you copy and paste here the script you're using?

---

### Post by CantankRus on 2016-07-06
It seems the showing of the titlebar buttons in cvlc is an issue with compiz/unity.
Unity doesn't use the gtk-window-decorator and draws it's own window decorations to incorporate menus.
If I use my gnome-flashback(metacity) session, cvlc works properly using the "--video-wallpaper" option.

---

### Post by Skaperen on 2016-07-06
w/o setting **DISPLAY** to the X display address, you can't run X apps.  in an rc script starting up the system, **DISPLAY** is not yet set.

---

### Post by Furycd001 on 2016-07-06
> **CantankRus said:**
> Also test the script by pasting into a terminal the same path used in startup applications.
You could also try delaying the start of cvlc by adding a sleep line to the script.
eg
```
#!/bin/bash

**sleep 5**
cvlc --play-and-exit --video-wallpaper --no-audio '/home/furycd001/Downloads/mex' '/home/furycd001/Downloads/mex1.mp4' '/home/furycd001/Downloads/mex2.mp4'
```
If that doesn't work try **sleep 30**.

Can you copy and paste here the script you're using?

I've pasted in my sh file below as requested. Running the cvlc command in terminal works perfectly fine and so does loading the sh file. It's just whenever I have either placed in my start-up list that it loads the full vlc app instead of setting as wallpaper. I will try adding the sleep part to my sh file when I'm next at my laptop. If it helps any I am running ubuntu mate on this laptop. I plan to try and accomplish the same thing soon on a ubuntu gnome laptop but I'm waiting on that getting fixed. Hope it will works much easier on that laptop.

--------------------


#!/bin/bash

cvlc --play-and-exit --video-wallpaper --no-audio '/home/furycd001/Downloads/mex.mp4' '/home/furycd001/Downloads/mex1.mp4' '/home/furycd001/Downloads/mex2.mp4

> **Skaperen said:**
> w/o setting **DISPLAY** to the X display address, you can't run X apps.  in an rc script starting up the system, **DISPLAY** is not yet set.

Is there a way to get around this and mskenit work ??

---

### Post by Furycd001 on 2016-07-09
Guys. I have not changed anything since my last post, but upon booting my laptop today everything appears to be working like it should be. Don't know what is up but yay it's working...

---


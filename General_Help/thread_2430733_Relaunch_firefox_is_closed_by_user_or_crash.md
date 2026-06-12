---
title: "Relaunch firefox is closed by user or crash"
date: 2019-11-06
forum: General Help
---

### Post by rboice on 2019-11-06
I am fairly new to Linux in general. I am trying to build a web kiosk and want the Firefox browser to relaunch if the user were to close it or if it were to crash. I have been all through the forums on this issue and none of the suggestions have worked out for me. Running Ubuntu 18.04.3 LTS and Firefox 70.0. I have tries all shell scripts and none of the seem to work. I cannot use the kiosk add-on for FF as for my needs it is inadequate. Any help would be greatly appreciated.

---

### Post by #&amp;thj^% on 2019-11-06
There is no "re-launch" (To my knowledge) command for firefox, the best I can guess is something along the lines of:
```
pkill firefox
firefox &
```

---

### Post by rboice on 2019-11-06
Thank you for your response. I am able to run a shell with the code you posted. Do know of a way to check if ff is open a and run that if it's not?

---

### Post by #&amp;thj^% on 2019-11-06
> **rboice said:**
>  Do you know of a way to check if ff is open a and run that if it's not?
There is a couple of ways, 
```
ps aux | grep firefox
```
Will give something like:
```
me          3253  0.0  0.0   4196  2640 ?        S    20:12   0:00 firejail firefox --proxy-server+localhost:8118
**me **         3254  0.0  0.0   4204  2388 ?        S    20:12   0:00 firejail firefox --proxy-server+localhost:8118
**me **         3263  4.1  2.9 2907764 350712 ?      Sl   20:12   0:44 /usr/lib/firefox/firefox --proxy-server+localhost:8118
**me **         3346  0.8  1.5 2548744 180936 ?      Sl   20:12   0:09 /usr/lib/firefox/firefox -contentproc -childID 1 -isForBrowser -prefsLen 1 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
**me  **        3417  0.7  1.8 27713004 217328 ?     Sl   20:12   0:08 /usr/lib/firefox/firefox -contentproc -childID 2 -isForBrowser -prefsLen 6443 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
me          3511  0.3  1.3 2476784 156840 ?      Sl   20:12   0:03 /usr/lib/firefox/firefox -contentproc -childID 3 -isForBrowser -prefsLen 7067 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
me          6128  1.4  1.2 2492304 151208 ?      Sl   20:14   0:13 /usr/lib/firefox/firefox -contentproc -childID 4 -isForBrowser -prefsLen 7562 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
**me**          6429  1.0  2.0 2642332 239896 ?      Sl   20:14   0:09 /usr/lib/firefox/firefox -contentproc -childID 5 -isForBrowser -prefsLen 7562 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
**me  **       27338  0.4  0.6 2398768 74568 ?       Sl   20:28   0:00 /usr/lib/firefox/firefox -contentproc -childID 6 -isForBrowser -prefsLen 7562 -prefMapSize 225852 -parentBuildID 20191031132559 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 9 true tab
**me  **       29135  0.0  0.0   6160  2268 pts/0    S+   20:30   0:00 grep firefox

```
Will even show the user using it, example on mine where** 'me' **is the user using Firefox.
also less obvious:
```
pgrep -u $LOGNAME firefox
```
it should return:
```
pgrep -u $LOGNAME firefox
**3263**

```
The **"3263"** (is what shows for mine) is a pid#/number, and will show only if Firefox is open.

---


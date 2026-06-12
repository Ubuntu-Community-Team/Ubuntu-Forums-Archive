---
title: "&quot;Maximum number of clients reachedCannot open display:&quot; kubuntu 22.04.1 LTS"
date: 2023-01-12
forum: General Help
---

### Post by draxavi on 2023-01-12
Since today, after some time I can't open anything. If I reboot I can open everything as usual.
 If i try to open in the terminal this is what I got:
 ```
"Maximum number of clients reachedThe futex facility returned an unexpected error code."

``` I did

 ```
sudo lsof | awk '/libX11.so/ {clients[$1]++;} END {for(c in clients){printf "%s\t%s\n", clients[c], c;}}'

``` and the result was
 ```
3       script-fu
3       kioslave5
3       at-spi2-r
2       plasma_se
3       kscreen_b
6       Socket
3       kglobalac
7       xdg-deskt
4       pulseaudi
23      WebExtens
82      steamwebh
1       xsettings
4       at-spi-bu
3       klauncher
14      dolphin
4       kdeconnec
4       DiscoverN
33      telegram-
789     Isolated
24      konsole
3       xembedsni
14      kwin_x11
34      Web\x20Co
8       kded5
1       kdeinit5
22      Privilege
3       kaccess
6       org_kde_p
2       startplas
3       RDD\x20Pr
11      gimp-2.10
44      steam
44      plasmashe
4       gsettings
18      systemset
3       ksmserver
6       kactivity
3       gmenudbus
14      polkit-kd
199     firefox
12      Xorg
4       Utility

```

Looked on other posts and didn't find anything that can really explain what is happening. any suggestion?

     

When I reboot it's seems it fixes for a short time, last time when my screen blocked it crashed the whole system, I could not get the error message but it was pointing a issue with the screen block.
Since when this issue happens, I can't do anything unless I closed something (this includes even shutdown or reboot), probably is related

---

### Post by MAFoElffen on 2023-01-13
> **draxavi said:**
>  
I did
```
sudo lsof | awk '/libX11.so/ {clients[$1]++;} END {for(c in clients){printf "%s\t%s\n", clients[c], c;}}'

``` and the result was
 ```

789     Isolated
199     firefox
82      steamwebh
44      steam
44      plasmashe
34      Web\x20Co
33      telegram-
23      WebExtens
24      konsole
22      Privilege

```
Looked on other posts and didn't find anything that can really explain what is happening. any suggestion?

     When I reboot it's seems it fixes for a short time, last time when my screen blocked it crashed the whole system, I could not get the error message but it was pointing a issue with the screen block.
Since when this issue happens, I can't do anything unless I closed something (this includes even shutdown or reboot), probably is related
If I'm ready that right, are you trying to figure out the number of screens that is being asked for by each application?

What it is, is that XServer has a fixed number of screens that It can divy out to applications. It is a very high number.

Every once in a while an application will leak and eat up screens, taking more than what is really needed, on run XServer to it's limit. Honestly, I haven't personally seen this error in about 8 years past.

Please post the results of 
```

sudo lsof 2> /dev/null | awk '"/tmp/.X11-unix/X0" {clients[$1]++;} END {for(c in clients){printf "%s\t%s\n", clients[c], c;}}' | sort -nr

```
I think that will show a truer picture of that...

---


---
title: "no Flash in Chromium (Firefox OK): &quot;Adobe Flash Player is required to display ...&quot;"
date: 2014-04-19
forum: General Help
---

### Post by sanderj on 2014-04-19
On a fresh install of Ubuntu 14.04, flash is not available in Chromium. Flash is working in Firefox.

Chromium says "Adobe Flash Player is required to display some elements on this page."

Ubuntu Software Center tells Flash is installed. Removing and re-installing does not solve the problem.

"chromium-browser --enable-plugins" does not change things

Details:

```
sander@hpi3:~$ ll /usr/lib/chromium-browser/plugins
total 18792
drwxr-xr-x 2 root root     4096 apr 19 07:35 ./
drwxr-xr-x 7 root root     4096 apr 15 19:47 ../
-rw-r--r-- 1 root root 19234160 apr 19 07:35 libflashplayer.so
sander@hpi3:~$ 
```


chrome://plugins/ (or about://plugins) does NOT show flash 

Tips how to solve this?

---

### Post by monkeybrain20122 on 2014-04-19
You need to install the package pepperflashplugin-nonfree from the repository. Since google has stopped supporting NPAPI plugins system flash no longer works in Chromium.

Good news is you may as well get the more up to date pepperflash, bad news is other media plugins have stopped working as well on Chromium and there is no fix
```
sudo apt-get install pepperflashplugin-nonfree
```

---

### Post by sanderj on 2014-04-19
Follow up: solved by installing pepperflash ... 

about://plugins now shows Flash, and everything is working.

---

### Post by sanderj on 2014-04-19
> **monkeybrain20122 said:**
> You need to install the package pepperflashplugin-nonfree from the repository. Since google has stopped supporting NPAPI plugins system flash no longer works in Chromium.

Good news is you may as well get the more up to date pepperflash, bad news is other media plugins have stopped working as well on Chromium and there is no fix
```
sudo apt-get install pepperflashplugin-nonfree
```

That worked indeed. Thank you.

"NPAPI plugins system flash no longer works in Chromium." ... oh, that sounds bad.

---

### Post by deadflowr on 2014-04-19
ninja'd.

---

### Post by sanderj on 2014-04-19
So ... does this mean that from now on, Chromium on Ubuntu 14.04 has no flash by default? If so: ... brrr.

And if so, wouldn't it be the solution from Ubuntu's side to say chromium-browser 'depends on' pepperflashplugin-nonfree, so that pepperflashplugin-nonfree gets installed by default as soon as chromium-browser is installed?

---

### Post by deadflowr on 2014-04-19
Yeah, it looks like to get flash on chromium you need to install pepper now.
Which is kind of a bummer, if you already go through the process of installing flash as usual.

Sort of redundant.

But the brightside is an updated version of flash, so glass half full.

---

### Post by carl4926 on 2014-04-19
sadly the pepper flash on my netbook doesn't work properly

---


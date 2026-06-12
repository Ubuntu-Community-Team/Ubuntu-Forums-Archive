---
title: "Crazy Flash Problem"
date: 2006-10-31
forum: General Help
---

### Post by nzk on 2006-10-31
I tried to install Flash 9 beta back in the 6.06 days (a week ago to be exact), and it worked fine, for a little while. Then mplayer and flash both didnt work AT ALL. I upgraded to edgy around this time, maybe that will fix it, but it didnt. So i uninstalled and reinstalled it, but no dice. Anyone know what is going on and how to fix it?

Thanks in advance.

---

### Post by nzk on 2006-11-05
Bump

---

### Post by aysiu on 2006-11-05
Can you explain exactly the steps you took to install Flash 9 beta?

Also, do they not work for all users on your Ubuntu installation? If you don't have a second user, create one, and see if that new test user has the same problem.

Do the plugins work for Epiphany? If not, install Epiphany and see.

Are you using the Mozilla build of Firefox or the Ubuntu one?

---

### Post by nzk on 2006-11-05
> **aysiu said:**
> Can you explain exactly the steps you took to install Flash 9 beta?

Also, do they not work for all users on your Ubuntu installation? If you don't have a second user, create one, and see if that new test user has the same problem.

Do the plugins work for Epiphany? If not, install Epiphany and see.

Are you using the Mozilla build of Firefox or the Ubuntu one?
Mozilla build. It doesnt work for a second user or for epiphany, i had tried that before. The steps I took are from [this site ]("http://linux.edu.lv/index.php?name=News&file=article&sid=244") (the second method)

---

### Post by aysiu on 2006-11-05
Can we try it a different way, then?

Close Firefox ```
sudo aptitude remove flashplugin-nonfree
sudo nano -B /etc/apt/sources.list
``` Remove these lines: ```
deb http://3v1n0.tuxfamily.org dapper 3v1n0
deb-src http://3v1n0.tuxfamily.org dapper 3v1n0
``` Save (Control-X, Y, Enter). ```
wget -c http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar -vxzf FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55/
sudo cp libflashplayer.so /usr/lib/firefox/plugins/
``` Start Firefox.

Any difference?

---

### Post by nzk on 2006-11-05
Nope :(

---

### Post by aysiu on 2006-11-05
Hm.

When you say Flash doesn't work at all, can you be more specific? What exactly happens when you try to visit a page that requires Flash?

Also, have you experienced the same problem if you install Flash 7 instead of Flash 9 beta?

---

### Post by nzk on 2006-11-05
> **aysiu said:**
> Hm.

When you say Flash doesn't work at all, can you be more specific? What exactly happens when you try to visit a page that requires Flash?

Also, have you experienced the same problem if you install Flash 7 instead of Flash 9 beta?

To test, I visit Youtube and thelookandfeelofperfect.com

Sometimes, the sites complain that I need to have both Javascript and Flash on. Othertimes, the little Firefox green puzzle piece shows, saying that I need to install flash.

Err how do I install Flash 7? I'd rather have that then nothing.

---

### Post by Ramses de Norre on 2006-11-05
```
sudo aptitude install flashplugin-nonfree
```

---

### Post by Cynical on 2006-11-05
Did you install firefox in a non standard directory like /opt?

---

### Post by aysiu on 2006-11-05
> **nzk said:**
> To test, I visit Youtube and thelookandfeelofperfect.com

Sometimes, the sites complain that I need to have both Javascript and Flash on. Othertimes, the little Firefox green puzzle piece shows, saying that I need to install flash.

Err how do I install Flash 7? I'd rather have that then nothing.
If you get the puzzle piece, try just installing the plugin the traditional way (this will install Flash 7 for now). We can worry about Flash 9 later.

This will help you:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by nzk on 2006-11-05
Firefox is in it's regular directory. Also the sudo aptitude install flashplugin-nonfree doesnt work :(

---

### Post by nzk on 2006-11-05
> **aysiu said:**
> If you get the puzzle piece, try just installing the plugin the traditional way (this will install Flash 7 for now). We can worry about Flash 9 later.

This will help you:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)
No dice :(

---


---
title: "flash won't work (I've tried everything)"
date: 2006-10-27
forum: General Help
---

### Post by flammen on 2006-10-27
OK, I've ready many of the threads about installing flash and tried all of them, but flash STILL won't work for me.  Every flash page I go to tells me I don't have flash and it doesn't show up in about:plugins

I've downloaded flash player 9 beta and copied libflashplayer.so to these folders

/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins
/home/kellen/.mozilla/plugins

I tried doing this as suggested in another thread..
"sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/"

but the first command failed and said no candidate version found


What am I doing wrong?

---

### Post by flammen on 2006-10-27
oh yeah.  I'm using Edgy Eft AMD64  with Firefox 2.0

---

### Post by SunnyRabbiera on 2006-10-27
maybe wine/crossover office might help you.

---

### Post by marcozs on 2006-10-27
Hi, 
I did not install flash-nonfree but I just estracted the libflashplayer.so (9.0) in ~/.mozilla/plugins and it works... try to remove the flash-nonfree and see what happens

---

### Post by flammen on 2006-10-27
just removed the flash-nonfree and it's still not working.  Thanks for the suggestion though.

---

### Post by marcozs on 2006-10-27
are you using edgy or dapper? what's in your .mozilla/plugins directory?

---

### Post by flammen on 2006-10-27
I'm using Edgy, and my .mozilla/plugins directory has libflashplayer.so in it.

---

### Post by marcozs on 2006-10-27
Same as me...
The process I followed was: I went to a website needing flash, Firefox asked me if I wanted to install the flash player and I answered yes so it installed the flash7... then I went in the plugins directory and replaced the libflashplayer.so of the v7 with the one from the archive you posted and restarted Firefox and it worked...

---

### Post by searayman on 2006-10-27
If you want flash 9, and how to install it go here:

[http://guidetolinux.wetpaint.com/page/Install+Flash+9+Alpha]("http://guidetolinux.wetpaint.com/page/Install+Flash+9+Alpha")

---

### Post by marcozs on 2006-10-27
> **searayman said:**
> If you want flash 9, and how to install it go here:

[http://guidetolinux.wetpaint.com/page/Install+Flash+9+Alpha]("http://guidetolinux.wetpaint.com/page/Install+Flash+9+Alpha")

It doesn't say much more than said in this thread, except to restart the system :)

---

### Post by flammen on 2006-10-27
yeah.  I restarted, and that didn't help.  

However, I did use synaptic to install libflash something or other and now I have flash 4.0 installed.  I then tried recopying the new libflashplayer.so back into those directories and it still doesn't work.

---

### Post by evilhomer on 2006-10-27
i had the same prob.  turned out a long time ago, i wanted a new ver of firefox that wasn't in the repo's yet, so installed it myself to /opt/firefox.  perhaps you did something like that?

---


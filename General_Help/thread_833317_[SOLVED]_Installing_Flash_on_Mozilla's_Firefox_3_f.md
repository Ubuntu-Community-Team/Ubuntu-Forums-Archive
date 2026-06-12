---
title: "[SOLVED] Installing Flash on Mozilla's Firefox 3 for 64-bit"
date: 2008-06-18
forum: General Help
---

### Post by Sim777 on 2008-06-18
Anyone know how to install flash on 686 and FF3? I'd like to move on to FF3 but without flash...

---

### Post by aysiu on 2008-06-18
> **Sim777 said:**
> Anyone know how to install flash on 686 and FF3? I'd like to move on to FF3 but without flash...
How did you install Firefox 3?

Did you download it from Mozilla? And, if so, did you link it to your plugin directory?

---

### Post by Sim777 on 2008-06-18
> **aysiu said:**
> How did you install Firefox 3?

Did you download it from Mozilla? And, if so, did you link it to your plugin directory?

I didn't really install it...I just run it from terminal from firefox folder with ./firefox command. And I don't use plugins so that has no adverse affect to me.

---

### Post by aysiu on 2008-06-18
> **Sim777 said:**
> I didn't really install it...I just run it from terminal from firefox folder with ./firefox command. And I don't use plugins so that has no adverse affect to me.
Well, you're asking how to install the Flash plugin, so you clearly want to use plugins.

Close Firefox.

Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/firefox/plugins ~/firefox/plugins.old
sudo ln -s /usr/lib/firefox/plugins ~/firefox/plugins
``` Then start Firefox again and visit a site that requires Flash and click on the *Install missing plugins* dropdown bar that appears.

---

### Post by Sim777 on 2008-06-18
> **aysiu said:**
> Well, you're asking how to install the Flash plugin, so you clearly want to use plugins.

Close Firefox.

Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
mv ~/firefox/plugins ~/firefox/plugins.old
sudo ln -s /usr/lib/firefox/plugins ~/firefox/plugins
``` Then start Firefox again and visit a site that requires Flash and click on the *Install missing plugins* dropdown bar that appears.

I have in, somehow, install it manually...  

> ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


---

### Post by aysiu on 2008-06-18
> **Sim777 said:**
> I have in, somehow, install it manually...
Oh, you're using 64-bit. That's a bit more complicated.

Try [this](http://ubuntuforums.org/showthread.php?t=772490), then.

---

### Post by itaintover on 2008-06-18
686 doesnt equal 64 bit...

---

### Post by aysiu on 2008-06-18
> **itaintover said:**
> 686 doesnt equal 64 bit...
Yes, also a good point.

---

### Post by Sim777 on 2008-06-18
I know my n00bness is strong.

---

### Post by Sim777 on 2008-06-18
OK. Problem fixed. I lunched script from this guide [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)
that installs flash for firefox2. But since I have FF3, it doesn't work. 
So ...

Then I copied /usr/lib/mozilla/plugins/libflashplayer.so to /firefox/plugins
and copied /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so to /firefox/plugins

/firefox/plugins  <- location of where I extracted tar from mozilla website. 

Hope this helps someone.

---


---
title: "problem with xscreensaver and freevo"
date: 2007-12-02
forum: General Help
---

### Post by swinky on 2007-12-02
I am having an odd sort of problem on my Freevo based media box, running Ubuntu 7.10. Freevo set up without error (for once, I think it is the third time I've set up Freevo and the first time I didn't get horrible, random errors) and works great.

My problem is trying to use a screensaver for Freevo. The built-in screensaver plugin works, but won't activate while the music player is running, so that option is out. I can get the freevoscreensaver plugin to run, but it doesn't work as it should. I installed xscreensaver with apt-get, but for some reason the screensaver won't initialize when I set it to use xscreensaver, so instead I tried using the script option to run scripts that will start xscreensaver and immediately activate the screensaver.

I set the screensaver to start after 15 seconds (for testing purposes,) and after the 15 seconds, it runs the scripts as planned. The problem is that when it runs /usr/bin/xscreensaver, rather than running as a daemon in the background, it runs in the terminal and stops the next command (/usr/bin/xscreensaver-command -activate) from being run. It also seems to stop input from lirc.

Now, I'm pretty new to the scripting thing (in fact, while I say "scripting" I really mean it's a three line file that has #!/bin/bash and then two files to run), so is there a way I can tell xscreensaver to run in the background? That's going to be the way I need to do this, IMO. I've tried running xscreensaver as a startup script, to execute before Freevo, but it fails because X isn't running yet. I can't run it after freevo starts, either, because freevo seems to halt all other startup scripts until freevo stops (took me a while to figure out why lirc wouldn't run for that reason!)

---

### Post by frenchn00b on 2008-02-17
Nice 

[http://doc.freevo.org/ScreenSaverPlugins/ScreenSaverPlugin](http://doc.freevo.org/ScreenSaverPlugins/ScreenSaverPlugin)

I am today trying the screensaver too
 
I'll post my end config.

that way;
SCREENSAVER_DELAY = 300 # of seconds to wait to start saver.
SCREENSAVER_CYCLE_TIME = 60 # of seconds to run a screensaver before starting another saver.
plugin.activate('screensaver')

 but at the end; it gives a black screen on its blue menu, but do not turn off the powersscreen of hte monitor, does it for you ,?

---


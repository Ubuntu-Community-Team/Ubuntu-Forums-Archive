---
title: "Miro crash"
date: 2008-02-17
forum: General Help
---

### Post by icechen1 on 2008-02-17
I searched the forums and there aren't any tread about this problem.
I just downloaded Miro 1.1.2 and it crashes and this is the output in the terminal:
```
icechen1@icechen1-laptop:~$ miro
/usr/lib/firefox
INFO     Starting up Miro
INFO     Version:    1.1.2
INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-1.1.2/tv/resources - 6194
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1202440018.67
INFO     Loading preferences...
INFO     Starting event loop thread
INFO     Restoring database...
INFO     Connecting to /home/icechen1/.miro/sqlitedb
TIMING   Database load slow: 0.156
INFO     Spawning auto downloader...
INFO     Displaying main frame...
WARNING  Menu item action "RenameVideo" not implemented
WARNING  Menu item action "FastForward" not implemented
WARNING  Menu item action "Rewind" not implemented
WARNING  Menu item action "UpVolume" not implemented
WARNING  Menu item action "DownVolume" not implemented
WARNING  Volume changed before videoDisplay created
WARNING  Display updated before video display was created
INFO     Creating video display...
INFO     loaded renderer 'xinerenderer'
INFO     *** Launching Downloader Daemon ****
INFO     First URL is https://www.miroguide.com/
TIMING   Icon clear: 0.003
INFO     Starting movie data updates
INFO     Finished startup sequence
TIMING   idle (finalizing startup) too slow (1.630 secs)
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
INFO     *** Daemon ready ***
INFO     got file:///tmp/tmpB4jRBE.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///tmp/tmpFR-VCL.html
INFO     First URL is https://www.miroguide.com/
INFO     got file:///usr/share/miro/resources/html/guide-navigation.html
INFO     First URL is https://www.miroguide.com/
INFO     got https://www.miroguide.com/
INFO     First URL is https://www.miroguide.com/
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
WARNING: u'None' has no scheme
WARNING: Assuming port 80 for scheme: 
/usr/bin/python2.5: symbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
WARNING  downloader: connection closed -- quitting
INFO     Shutting down downloaders...



```
I can see it is a java problem.Anyone have the same problem?

---

### Post by trippinnik on 2008-02-17
maybe it's a java problem, you could try installing icedtea
> ymbol lookup error: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so: undefined symbol: PR_NewMonitor
I remember that a while back you needed to install icedtea if you wanted to install Miro at all.

---

### Post by Azraelthe7th on 2008-02-18
That worked for me!  Thanks!

---

### Post by tj111 on 2008-02-19
Same problem here.  Installing the icedtea and icedtea-jre in synaptic didn't help either.

---

### Post by tj111 on 2008-02-19
Edit: spoke to soon.  Forgot to get the icedtea-plugin.  That seemed to do the trick, thanks!

---


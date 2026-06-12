---
title: "System log lists multiple danger warnings"
date: 2018-12-21
forum: General Help
---

### Post by Gnusboy on 2018-12-21
Dec. 21, 2018
 
 
 Hey y'all
 
 
 I was just scanning a document and my system slowed down showing a gray screen, and them went back to the normal view. It didn't freeze, or lock - it was just brief couple of moments.
 
 
 It's been my understanding that this happens when there is a large draw from the RAM. This seems to happen under many different situations - too many windows open or while streaming music, etc. But it also happens even when there is not an extreme draw on the system, which is how it just happened.
 
 
 I'm pretty ignorant of the system log. I check it now and then, but I don't understand how to read it.
 I captured today's event from the system log, which shows multiple warnings.  
 
 
 I have seen these types of warnings and many others at different times. Some warnings seem to be more important than others, but again ??
 
 
 So, my question is; what is the cause of the screen "dim-out" in various situations and is it important?
 
 
 My system is often fluky - in many different ways and it's growing older. I built it myself in about 2010, so I'm past due for a new one. But this one has to make do for a while longer.
 
 
 Here's what I'm running:
 AMD 64 Phenom quad core
 4GB Ram
 650 GB hard drive, less than half full
 
 
 
 
 These are the types of entries I see when I look at the log. I would appreciate any help in basic understanding for these events. Thanks.
 
 
 ```

 Dec 21 13:22:51 ranha-system systemd-timesyncd[506]: Synchronized to time server 91.189.94.4:123 (ntp.ubuntu.com).
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 561: released ff/cc/0 interface
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 975: removed HP-LEDM-SCAN channel=24 clientCnt=0 channelCnt=0
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 960: new HP-LEDM-SCAN channel=24 clientCnt=1 channelCnt=1
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 427: Found interface conf=0, iface=0, altset=0, index=11
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 389: Active kernel driver on interface=0 ret=0
 
 
 
```
 
 
 ```

 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 535: claimed ff/cc/0 interface
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 561: released ff/cc/0 interface
 Dec 21 13:23:01 ranha-system simple-scan: io/hpmud/musb.c 975: removed HP-LEDM-SCAN channel=24 clientCnt=0 channelCnt=0
 Dec 21 13:23:56 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 
```
 
 
 ```

 
 
 Dec 21 13:23:56 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'sc': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 
 
 Dec 21 13:24:01 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 
 
 Dec 21 13:24:01 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'y': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 
```
 
 
 ```

 
 
 Dec 21 13:24:01 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:24:01 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'ys': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 Dec 21 13:24:08 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:24:08 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'y': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 
```
 
 
 
 
 ```

 
 
 Dec 21 13:24:09 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:24:09 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 's': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 
 
 Dec 21 13:24:10 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:24:10 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'sy': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 
 
 Dec 21 13:24:15 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
 Dec 21 13:25:10 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
 Dec 21 13:25:20 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
 Dec 21 13:25:31 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
 Dec 21 13:25:31 ranha-system systemd-timesyncd[506]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
 
```
 
 
 ```

 
 
 Dec 21 13:37:48 ranha-system dbus[1376]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
 Dec 21 13:37:48 ranha-system systemd[1]: Starting Hostname Service...
 Dec 21 13:37:48 ranha-system org.gtk.vfs.Daemon[2113]: ** (process:2527): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
 Dec 21 13:37:48 ranha-system org.gtk.vfs.Daemon[2113]: message repeated 4 times: [ ** (process:2527): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)]
 Dec 21 13:37:48 ranha-system org.gtk.vfs.Daemon[2113]: ** (process:2527): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
 Dec 21 13:37:48 ranha-system dbus[1376]: [system] Successfully activated service 'org.freedesktop.hostname1'
 Dec 21 13:37:48 ranha-system systemd[1]: Started Hostname Service.
 Dec 21 13:38:10 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
 Dec 21 13:38:22 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
 Dec 21 13:39:03 ranha-system gnome-session[2262]: (nautilus:2423): GnomeDesktop-WARNING **: Unable to create loader for mime type application/pdf: Unrecognized image file format
 Dec 21 13:39:03 ranha-system gnome-session[2262]: (nautilus:2423): GnomeDesktop-WARNING **: Error creating thumbnail for recent:///026ad08f4ea45508f66cc8bd5c1d5d74: Unrecognized image file format
 
 
 
```
 
 
 Dec 21 13:39:37 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
 Dec 21 13:39:47 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.91.157:123 (ntp.ubuntu.com).
 Dec 21 13:39:56 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:39:56 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'b': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 Dec 21 13:39:57 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:39:57 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'ba': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 Dec 21 13:39:57 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:39:57 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'bac': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 [/code]
 
 
 
 
 ```

 Dec 21 13:39:58 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to search index: Db block overwritten - are there multiple writers?
 Dec 21 13:39:58 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: (unity-files-daemon:4318): unity-files-daemon-WARNING **: daemon.vala:491: Error performing global search 'back': GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._g_2dio_2derror_2dquark.Code36: GDBus.Error:org.gnome.zeitgeist.EngineError.DatabaseError: Db block overwritten - are there multiple writers?
 Dec 21 13:40:02 ranha-system org.gnome.zeitgeist.SimpleIndexer[2113]: ** (zeitgeist-fts:2642): WARNING **: Failed to commit changes: Db block overwritten - are there multiple writers?
 Dec 21 13:40:29 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com)
 ]: Timed out waiting for reply from 91.189.89.198:123 (ntp.ubuntu.com).
 
```
 
 
 ```

 
 
 Dec 21 14:01:49 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.94.4:123 (ntp.ubuntu.com).
 Dec 21 14:02:00 ranha-system systemd-timesyncd[506]: Timed out waiting for reply from 91.189.89.199:123 (ntp.ubuntu.com).
 Dec 21 14:03:05 ranha-system systemd-timesyncd[506]: Synchronized to time server 91.189.91.157:123 (ntp.ubuntu.com).
 Dec 21 14:03:05 ranha-system systemd[1]: Time has been changed
 Dec 21 14:03:05 ranha-system systemd[2023]: Time has been changed
 Dec 21 14:04:27 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: ** (soffice:5456): WARNING **: Unknown event notification 36
 Dec 21 14:17:01 ranha-system CRON[5571]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
 
 
 Then there is this:
 
 
 Dec 21 14:04:27 ranha-system com.canonical.Unity.Scope.LocalFiles[2113]: ** (soffice:5456): WARNING **: **Unknown event notification 36**
 
 
 Dec 21 14:17:01 ranha-system CRON[5571]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
 
```

---

### Post by CatKiller on 2018-12-21
> **Gnusboy said:**
> So, my question is; what is the cause of the screen "dim-out" in various situations and is it important?

It means that the process isn't responding to requests from the window manager. The dimming is simply an indicator.

It could be because the process has crashed, or it's waiting for the processor to finish what it's doing, or it's waiting for file I/O.

Your errors are about the activity logger. I personally wouldn't like that running at all, but I also wouldn't be keen on it running all the time on a system that was a bit too long in the tooth. You can probably turn it off.

---

### Post by Gnusboy on 2018-12-21
Thanks for the tip. I've never heard of the activity logger. Where can I find it and turn it off?

---

### Post by CatKiller on 2018-12-22
There's probably a setting in the system settings about activity logging. I don't use Gnome, so I wouldn't be able to tell you what it was called. The program itself is called Zeitgeist, so you should be able to search for information about it.

---

### Post by dragonfly41 on 2018-12-22
Launching System Monitor > Processes window

I see a process running

sh
|---zeitgeist-daemon

You can select this process and end it running.

---

### Post by Gnusboy on 2018-12-22
Hey all

It appears that a system activity monitor could be impacting the screen gray outs. When I went to adjust that setting, I saw a curious situation with the running system processes.
From what I see, there are many processes running at 100% Only  three are at lower usage. I tried shutting down some of my work, but it didn't change the usage.
It is eating almost half of my ram. Can you  tell me what this is and if it's significant? 
My system often runs  slower than I expect. And is it a possible cause of my gray screen slow  downs?

Here's a screen grab of what I see.

---

### Post by CatKiller on 2018-12-22
> **Gnusboy said:**
> It appears that a system activity monitor could be impacting the screen gray outs. 

It could be, sure, if it's calculating stuff so there isn't enough processor left over for your process, or if it's slowing down disk access so the process needs to wait longer. Or they could be unrelated. Either way, the grey screens are just an *indicator* that the computer is busy, not really a problem in themselves.

> When I went to adjust that setting, I saw a curious situation with the running system processes.
From what I see, there are many processes running at 100% Only  three are at lower usage. I tried shutting down some of my work, but it didn't change the usage.

Your screenshot isn't a list of processor usage, it's a list of storage usage. It shows that the snap applications exactly fit in the snap containers, which is not terribly interesting. It also shows that you have plenty of hard drive space left on your three partitions, which is good.

> It is eating almost half of my ram.

You've not shown your RAM usage but, in general, empty RAM is wasted RAM. If the RAM is sitting empty, the system will tend to fill it with file cache, so that file access is quicker. RAM access is orders of magnitude quicker than hard drive access. Doing so doesn't negatively affect performance, since writing the new data over file cache and writing new data to empty RAM takes exactly the same amount of time.

>  Can you  tell me what this is and if it's significant? 
My system often runs  slower than I expect. And is it a possible cause of my gray screen slow  downs?

Here's a screen grab of what I see.

Again, the grey screens are an indicator of your computer being slow, not a cause.

The initial condition you reported when you got the inactive window notification was when you were scanning, but that's exactly the kind of situation where you'd expect the window to go inactive. The program desperately wants to put all those pixels into an image, but it can't do that until it's received the pixels from the scanner, and scanners are slow.

So far, it seems to simply be that your computer is just a bit too slow for the things it's being asked to do. If it were mine, I would try to stop it running things that it didn't need to, like the activity logger, and maybe switch to a less-demanding desktop environment, like LXDE.

---

### Post by Gnusboy on 2018-12-23
Catkiller

I gotta say thank you for your help.
You truly helped me to understand more about my system and what's going on. I appreciate it.

But, P.S. ... my cat can kill your cat. When she's on the ol' eggnog, you gotta be careful. Happy holidays.

---


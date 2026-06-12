---
title: "Basic backing up chrome browser"
date: 2017-08-31
forum: General Help
---

### Post by Kris_M on 2017-08-31
I know and trust clonezilla but also looking for something in Ubuntu.(17.04 Gnome)

When I tried this before with chromium and tried to restore something I got mixed results, not just a clean image (deja and backintime) - the browser would have half of some things and not others.

Initially set up deja to backup /.config/google-chrome on demand. But thinking I should change that to /kris and exclude games. or / and exclude games.

My worry is losing the 133 tabs from some chrome or Tiny Suspender crash (Great suspender killed me, but this was a month ago when I was playing with chromium. Now chrome.

I chose deja and/or backintime because they are gui and thus easy for me to work with.  But I think the question is how to set them up. Do I need some stuff in / ? I am guessing probably.

---

### Post by TheFu on 2017-09-01
All user settings are stored in ~/. If you back up your HOME, that will get everything.  The only time settings for a user wouldn't be in ~/ is if YOU specifically went way out of your way to place them somewhere else.  Way, way, way, out of your way.

There is a GUI tool, **aptik**, to backup just HOME and some theme settings elsewhere.  
[http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/](http://ubuntuhandbook.org/index.php/2017/01/aptik-backup-ppa-installed-apps-users-data/)

Of course, you can keep using back-in-time or dejadup, if you like. I wouldn't use both.

I backup everything in my HOME except any cache directories.  Everything else is relatively tiny, so avoiding it doesn't make much sense - at least for me.  If you keep media files under your HOME, it may make sense to ignore those directories too.

---

### Post by Kris_M on 2017-09-01
Thanks! For some reason I can't get root Back in Time to run (seems to start, then nothing), so will use LuckyBackup root which is about the same. Will not use deja. Will back up Home, excluding games. Will image occasionally with Clonezilla until I am sure this works. I'll go take a look at aptik and maybe run parallel. I put backups on my work partition which is on another spindle and ext4. Do folks normally put it in home and then add it to exclude list? THANKS!

---


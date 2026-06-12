---
title: "Synch Tomboy Notes with Google Drive or Webdav"
date: 2014-12-22
forum: General Help
---

### Post by afrodeity on 2014-12-22
At some point Ubuntu One dropped Tomboy support. 

(One of the many 'putting away the crayons and turning Ubuntu into a broken pencil that sells pencil sharpeners' move by the MOTU)

The app still carries the Ubuntu one plugin, which is packaged with just two synchronization plugins, the first one, the **local directory synchronisation,** the other, the ** web synch service** which accommodates hosted tomboy servers.

Various tutorials exist on how to synch notes using dropbox, the web is littered with them, but what if you don't want to use dropbox?

What if you think dropbox is as glitchy and regressing as Ubuntu One?

What if you can't find a free tomboy server? Or want to use [google-drive]("http://drive.google.com") or a free [webdav server]("http://www.free-online-backup-services.com/features/webdav.html") like webdav.4shared.com?

There should be a [plugin ]("https://wiki.gnome.org/Apps/Tomboy/PluginList")for this.

But there isn't.

UPDATE: While I'm looking for a solution, either write a webdav plugin, figure out a method of storing on google drive, I found this: [http://www.getsync.com/how-it-works]("http://www.getsync.com/how-it-works")

---

### Post by afrodeity on 2014-12-22
> this synchronisation addin is not supported on your computer. Please make sure you have FUSE and wdfs correctly installed and configured

trying to get a webdav plugin to work

---

### Post by afrodeity on 2014-12-22
[http://askubuntu.com/questions/254241/gnote-tomboy-webdav-connecting-error](http://askubuntu.com/questions/254241/gnote-tomboy-webdav-connecting-error)

---

### Post by afrodeity on 2014-12-22
bug in webdav plugin [http://ubuntuforums.org/showthread.php?p=9220566](http://ubuntuforums.org/showthread.php?p=9220566)

---

### Post by dragonfly41 on 2014-12-22
I use SpiderOak .. not Google Drive or WebDav 

You can try this  ...

Create a new personal (free for 2GB) account with SpiderOak ... [https://spideroak.com](https://spideroak.com)

When you run SpiderOak a sync folder is created as SpiderOak Hive.

Copy ~/.local/share/tomboy into a folder in SpiderOak Hive

Open Tomboy > Preferences > Folder Path > path to SpiderOak Hive

Sync from Tomboy <--> SpiderOak Hive
and
Sync from SpiderOak Hive <--> remote SpiderOak

...

comparison here ... [Google Drive vs. SpiderOak: Side-by-Side Comparison]("https://googledrive.knoji.com/compare-vs/spideroak/")

---


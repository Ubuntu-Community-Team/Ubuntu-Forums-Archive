---
title: "Automatically sync laptop and desktop when they are networked?"
date: 2013-06-08
forum: General Help
---

### Post by schooner on 2013-06-08
I've seen several almost-solutions to this but nothing quite as simple and automatic as I'm looking for:

When I log into either my desktop or my laptop, I'd like it to check automatically (I don't want to have to click or type anything) whether the other computer is present on the (WiFi) network and, if it is:
(1) synchronize a set of pre-configured files and folders (data, email, bookmarks, contacts, etc);
(2) keep synchronizing while I work; and
(3) make sure they are synchronized when I log out, even if it means delaying the log-out until it's done.

My desktop and laptop run the same distro/desktop (edubuntu/xfce 12.04) but have different architectures (i386/x86_64).

I tried Ubuntu One and gave up when it took a week to upload 10 GB of data.  (Broadband upload speeds are pitiful where I live.)  It would fail on a common use case of log in, do email, log out (which changes my Inbox, Trash and Sent folders for example) because it would be too slow to sync those file before I logged out.

Some other near misses I found googling around:
Unison: [https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)  [http://ubuntuforums.org/showthread.php?t=908914](http://ubuntuforums.org/showthread.php?t=908914)
OneConf: [https://wiki.ubuntu.com/OneConf/](https://wiki.ubuntu.com/OneConf/)
NFS + rsync + scripts: [http://ubuntuforums.org/showthread.php?t=2152406](http://ubuntuforums.org/showthread.php?t=2152406)

This sounds like such a common need I'm sure there is a solution: has anyone here spotted what I missed?

---

### Post by johsch on 2013-06-08
[I]
When I log into either my desktop or my laptop, I'd like it to check automatically (I don't want to have to click or type anything) whether the other computer is present on the (WiFi) network and, if it is:
(1) synchronize a set of pre-configured files and folders (data, email, bookmarks, contacts, etc);
(2) keep synchronizing while I work; and
(3) make sure they are synchronized when I log out, even if it means delaying the log-out until it's done.
[/I]
I have exactly this problem!  Please no complicated scripts, cron, etc.

---


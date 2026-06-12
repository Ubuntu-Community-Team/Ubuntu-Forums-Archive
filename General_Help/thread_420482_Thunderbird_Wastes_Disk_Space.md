---
title: "Thunderbird Wastes Disk Space"
date: 2007-04-23
forum: General Help
---

### Post by wsmoser2004 on 2007-04-23
I"m not really sure where to put this...but General Help seemed like a good place :).

I use Mozilla Thunderbird for all of my E-mail, and it's configured for POP mail.  However, even though I delete most of the E-mail I get, Thunderbird seems to cache all of it.  If I go into ~/.thunderbird folder and poke around a bit, I can find files called "Inbox", "Sent", and such in the various directories that take up sometimes upwards of 80 MB of space.  This shouldn't be a problem, but I'm a little bit tight on disk space, so I need everything I can get.  Does anyone know how to disable this "feature" of Thunderbird?

I suppose an alternate option would be to delete Windows, since that's consuming the better part of my hard disk.  Unfortunately I still need it...

Thanks in advance for any advice!

---

### Post by NT4usB on 2007-04-23
In Thunderbird, deleted files aren't really deleted until you compact the folders. 
Click to highlight the account you want to compact. Select File>Compact folders.
Alternately, Right click>Compact on individual folders.
There is a setting under Edit>Preferences>Advanced, Offline and disk space flag.
Check the box to compact and bump the number in the fill box up to 10000 or so, or it will nag you constantly...

ed: clarificating... You right click>compact the folders in Thunderbird. Inbox, Sent, Trash, etc. Not the filesystem folders.

---

### Post by wsmoser2004 on 2007-04-24
NT4usB-

Wow, thanks...that worked great!  For some reason I was reading "compact folders" as "compress folders" and I didn't want it to be slow...but I'm glad I found that feature.  

I've been using Thunderbird for over a year now...and my previous "solution" was to go in and delete those files from the disk (a very poor solution indeed)...but this solution works so much better.  Thanks!

-wsmoser2004

---


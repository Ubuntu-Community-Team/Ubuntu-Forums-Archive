---
title: "Rtorrent setup help."
date: 2007-08-17
forum: General Help
---

### Post by Leonin on 2007-08-17
I decided to switch from Azureus to Rtorrent since Azureus keeps crashing from time to time. 
I have some troubles with the setup though. I blame it on my stupidity :p
I have lots of downloaded torrents that I want to keep seed. They are located in: > home/mikael/Seed
How do I make Rtorrent seed them when I start it and not redownloading them once more
My torrent files are located in:
>  /home/mikael/torrents

I guess its somewhere in these sections (I have some trouble understanding what exactly they do)

> # Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
#session = ./session
or/and
> # Default directory to save the downloaded torrents.
#directory = ./
or/and
> # Watch a directory for new torrents, and stop those that have been
# deleted.
#schedule = watch_directory,5,5,load_start=./watch/*.torrent
#schedule = untied_directory,5,5,stop_untied=





Thank you for your time helping me. 

/Leonin

---

### Post by mali2297 on 2007-08-17
Given your information, I think you should do the following changes:

> 
# Default directory to save the downloaded torrents.
directory = ./Seed


and 

> 
# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=./torrents/*.torrent
schedule = untied_directory,5,5,stop_untied= 


respectively.

That should do it.

Also, *screen* is a nice tool to use with rtorrent. Look it up.

---


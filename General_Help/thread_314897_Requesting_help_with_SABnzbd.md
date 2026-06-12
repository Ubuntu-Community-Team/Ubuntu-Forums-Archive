---
title: "Requesting help with SABnzbd"
date: 2006-12-08
forum: General Help
---

### Post by chris1983 on 2006-12-08
Hi everyone, this is my first post. :)

I just decided to try Linux a few days ago and have installed Ubuntu 6.10.  I have managed to set up most of the things that I want, and I am very impressed with Ubuntu!

However, I am having some trouble setting up my favourite Usenet downloader, which is SABnzbd.  I have managed to get it installed (using [This guide]("http://drbyte.wiki.xs4all.nl/index.php?title=drbyte:Community_Portal#Installation_SABnzbd") as help.  I have configured all the options for my server, but it is unable to connect to the server.

I checked the Log file and the error seems to be here:
> 
2006-12-08 13:54:55,960::INFO::[downloader] [email]1@news-europe.giganews.com[/email]/:80: Initiating connection
2006-12-08 13:54:55,981::ERROR::[downloader] Failed to initialize [email]1@news-europe.giganews.com[/email]/:80
Traceback (most recent call last):
  File "/home/chris/sabnzbd/sabnzbd/sabnzbd/downloader.py", line 188, in run
    nw.init_connect()
  File "/home/chris/sabnzbd/sabnzbd/sabnzbd/newswrapper.py", line 66, in init_connect
    self.server.username, self.server.password)
  File "/home/chris/sabnzbd/sabnzbd/sabnzbd/newswrapper.py", line 39, in __init__
    raise socket.error(_errno, strerror)
error: (-2, 'Name or service not known')

Does anyone have any advice as to what might be going wrong?
Thanks in advance and apologies if this is in the wrong forum!

Chris.

---


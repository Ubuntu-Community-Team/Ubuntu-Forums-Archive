---
title: "Help extracting a multi-disk zip file"
date: 2007-06-29
forum: General Help
---

### Post by lbarnar on 2007-06-29
I wanted to try and run WOW on Ubuntu, so I downloaded WOW from direct2drive since that is where I originally bought the game.  It downloads as one large zip file.  When I try to extract it, I encounter this error:
An error occurred while loading the archive.
When I hit the command line output I get:

[/home/lee/Desktop/wowclientdd.zip]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/lee/Desktop/wowclientdd.zip or
          /home/lee/Desktop/wowclientdd.zip.zip, and cannot find /home/lee/Desktop/wowclientdd.zip.ZIP, period.

I understand what I is saying, but have no clue how to proceed.  Any ideas?
Thanks,
Lee

---

### Post by pickarooney on 2007-06-29
Download incomplete, is my bet. Check the filesize of what's on your disk against the file size on the web/ftp site.

---


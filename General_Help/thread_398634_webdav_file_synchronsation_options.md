---
title: "webdav file synchronsation options"
date: 2007-04-01
forum: General Help
---

### Post by willnapier on 2007-04-01
Hi. I have just signed up with fastmail.fm, who offer 1Gb of file storage, including the option of having a webdav folder. What I would really like to do is to be able to save files locally on my pc in the normal way, and for all files to be synchronised automatically. I have been looking for a webdav client, and have found that the konqueror browser (I am using Kubuntu) can access webdav files directly by using 'webdav://'. This enables copying etc, but I don't see a way to synchronise. Here are the thoughts I have so far after googling for a while:

I could get synchronex [http://www.xellsoft.com/SynchronEX.html]("http://www.xellsoft.com/SynchronEX.html")

This does exactly what I'm after. However it is not free or open source, and I want to find an equivalent (at least in respect of its webdav synchronisation) that is at least free, and hopefully open source too.

If there is not such a thing, is there a way to write some kind of bash script (I wouldn't mind learning how to do this if it would work this way) that would automate the otherwise repetitive task of copying the file you have saved up into the webdav folder? Or, perhaps some script or method that saves a file to two locations with one click?

Another software that does this sort of thing well is ifolder, which seems to be free but not open source, and requires the server that hosts the webdav folder to be ifolder enabled (which I don't think mine is).

I would be very grateful for any help on this. It would be so cool to have this feature. It would be like having imap for your files and folders, giving portability and backup.

Will

---

### Post by 23meg on 2007-05-04
[Conduit]("http://www.conduit-project.org/") should work with WebDAV, since it uses GnomeVFS for its "File" datatype, which in turn abstracts transfer protocols such as FTP and WebDAV.

---

### Post by willnapier on 2007-05-15
23meg Thank you very much for this. This looks exactly what I have been wanting and more. I will download and see if I can get it working.

Will

---


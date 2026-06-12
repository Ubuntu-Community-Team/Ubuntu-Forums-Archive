---
title: "Disk Station Replacement"
date: 2013-01-31
forum: General Help
---

### Post by gavinjb on 2013-01-31
Hi,

I am in the planning process of moving from an old QNAP NAS to having a Ubuntu Server and so far have found most of the software I need (and am currently doing a test build with Virtualbox), but have been unable to find any software to perform one task.

What I am looking for is to have a web based service that you can log onto and then enter HTTP/FTP/bit torrent address that will then be downloaded to a folder on the server.

I have found this very useful in the past when I want to 
1. Download large files  
2. Download files overnight with my PC powered off
3. Download files to my Server from work

Does anyone know anything which can do this, I have seen several Bit-torrent apps that can run as a Daemon and do this, but the ones I have looked at so far don't have the option for FTP/HTTP which I use more often than bit torrent.

Thanks,



Gavin,

---

### Post by tgalati4 on 2013-01-31
If you are going to log into your server remotely via ssh, then you can simply change directory to the desired download directory and use wget.

```
man wget
wget URL
```

Unless I am missing something.  You can use the *at* command to make it happen at a specific time.  *wget* will handle all three of your use cases.

---

### Post by gavinjb on 2013-01-31
Thanks, but ideally I would like a nice web interface, if I cant find anything I might have a go and see if it is possible to write a simple web interface that accepts the HTTP/FTP location and then calls wget.

If I can do that I will see if I can stick a secure log on onto it, but I am lazy and would rather use something someone else has written :)

---

### Post by papibe on 2013-01-31
Hi gavinjb.

Take a look at [FatRat]("http://www.webupd8.org/2010/03/fatrat-is-amazing-linux-download.html"), [pyLoad]("http://pyload.org/") and [JDownloader]("http://jdownloader.org/").

Regards.

---

### Post by gavinjb on 2013-02-02
Thanks, that helped a lot, how did you find them, I spent ages googling the other day and couldn't find much!

---


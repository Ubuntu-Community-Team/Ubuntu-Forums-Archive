---
title: "File downloading memory leak"
date: 2007-02-24
forum: General Help
---

### Post by ianthepetrock on 2007-02-24
Im running dapper drake desktop edition but i uninstalled gnome and related programs and use it as a server. I have apache2 and vsftpd installed. Whenever i start to download a file, even just a webpage, some ram is lost...and lot of ram is last when i start downloading a 200mb video file, ram usage goes up and doesnt go down after finishing downloading. This happens through ftp and apache directory listings. This is a big problem as i start with about 500mb of ram available but as i use my website, i get down to 14mb of ram available very fast and it hovers that low forever until i restart the server.

:mad: :confused: 

Any help is greatly appreciated

---

### Post by DagMan on 2007-02-24
Maybe this how to on doing the reverse of what you did can help in the way of cluing you in on what else to remove though I'm not sure it would be your problem.
[http://doc.gwos.org/index.php/LightweightGnome](http://doc.gwos.org/index.php/LightweightGnome)

Also since you started with a desktop machine and not the server install, perhaps you can find some services that you don't need and free up some more ram.  This is a better tool than BUM in my opinion as it finds more services.
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

My computer hasn't ever had perfect memory management but I've never just had it as a server.  I wonder if you'd go better with a server install disk the next time you upgrade or if it would be a problem there too.

---

### Post by ianthepetrock on 2007-02-24
Thanks but ..

The strange thing is that when i boot, i have plenty of ram like a regular server install, but as soon as i start downloading stuff or loading pages it goes down each download/page.  Im relunctant to install the server edition because i have GBs of files and some tricky configurations set up right now.

---

### Post by jringoot on 2007-03-08
> **ianthepetrock said:**
> Thanks but ..

The strange thing is that when i boot, i have plenty of ram like a regular server install, but as soon as i start downloading stuff or loading pages it goes down each download/page.  Im relunctant to install the server edition because i have GBs of files and some tricky configurations set up right now.

Where you able to resolve it?
I am using feisty fawn.
Since saturday I have also a memory leak, apparently caused by apt-get.
When apt-get is downloading installing, memory usage is rapidly climbing and afterwards it is still in use when apt-get is finished.
If someone knows a procedures to troubleshoot memory leaks or knows somekind of memory garbage collector in linux like ther is in the Java VM.
Please tell.

Thanks ahead,

Joost

---


---
title: "Cups server failed"
date: 2006-10-13
forum: General Help
---

### Post by coolclassic on 2006-10-13
This is the error I get whilst attempting to restart print server.

Unable to retrieve the printer list. Error message recevied from manager:

Connection to cups server failed. check that the cups server is correctly installed and running. Error: localhost: read failed(15)

I attempted localhost:631 but I got repeated "error" no info

---

### Post by Chareos on 2006-10-13
I opened
[https://launchpad.net/distros/ubuntu/+bug/65901](https://launchpad.net/distros/ubuntu/+bug/65901)

---

### Post by coolclassic on 2006-10-17
My problem is solved found help in kubuntu forums here is the link:

[http://kubuntuforums.net/forums/index.php?topic=9959.0](http://kubuntuforums.net/forums/index.php?topic=9959.0)

---

### Post by Chareos on 2006-10-18
> **coolclassic said:**
> My problem is solved found help in kubuntu forums here is the link:

[http://kubuntuforums.net/forums/index.php?topic=9959.0](http://kubuntuforums.net/forums/index.php?topic=9959.0)


THANKS !

---

### Post by msak007 on 2006-10-21
I get a similar CUPS server error, but the details of mine is "Error: the IPP request failed for an unknown reason." This also started after the KDE 3.5.5 update. I tried the fix you linked to but it didn't resolve it. I've searched here and googled it, but it seems not many people get this error and the ones that do have no fix or workaround. Anybody have any other suggestions?

---

### Post by coolclassic on 2006-10-22
It may be that you are doing something wrong i.e when I tried to put the ip address in the first time I got the error you are getting.

The ip address should replace hostname and you should leave port as 631 remember then to add printer using printmanager.

I also reinstalled cups I don't know whether that was needed.

---


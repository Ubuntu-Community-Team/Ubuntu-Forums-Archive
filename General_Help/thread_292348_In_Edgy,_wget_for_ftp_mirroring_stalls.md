---
title: "In Edgy, wget for ftp mirroring stalls"
date: 2006-11-03
forum: General Help
---

### Post by tassou on 2006-11-03
Hello,

I have been using a networked backup solution based on wget and ftp for a few months in ubuntu 5.10 "Breezy". It is based on the presence of my laptop in the local network, which triggers the following command once a day on the backup server:
 ```
wget -nH -np -o log-wget --no-passive-ftp -m ftp://archive@192.168.0.50/
```
For those not familiar with wget syntax, it reads the whole ftp server root on my laptop, and retrieve files that appears to have been modified, plus new files.

Well, it used to work and still works perfectly in Breezy, with wget version 1.10, but in Edgy, with wget version 1.10.2, the connection is dropped in the middle of the task, with no predictable pattern. The ftp server gives the following reason :
```
425 Can't build data connection
```.

The laptop that has to be backuped is running windows, with filezilla ftp server, last version.

The backup server is running edgy since 3 days, after a year on Breezy.

I have two more laptop, one is still running Brezzy, and can perform the backup command with no problem, and the other is running Edgy, and can NOT perform the backup process for the same reason as with the backup server.

**Therefore, it appears that Edgy is responsible for this connection drop.**

I tried to downgrade wget to version 1.10 in Edgy and I still get the same error, it seams that at a point, the backup machine is not responding when running Edgy. Once again, this does not happen with Breezy.

This is really confusing, nothing appears in edgy logs, I can really not figure what is happening.

Any help would be very valuable.

Thanks !

---

### Post by catlett on 2006-11-03
I just found this 

> You normally get this error if you are trying to upload from behind a firewall. If that is the case, you should set your FTP client to use Passive transfer mode. We believe that FrontPage 2000 doesn't support passive transfer mode at this time.
Could it be possible that Edgy doesn't support passive transfer mode or that  passive transfer is disabled by default? Sorry to not have any expertise on the subject but I was just looking for something different in Edgy. Somehow Edgy is blocking the upload, but how?

..............................................................................................................................................................................................
I also found this in a BSD mailing thread.
> Michael P McIntyre wrote:

> ftp> ls
> 227 Entering Passive Mode (204,111,12,156,183,117)
> 200 PORT command successful.
> 425 Can't build data connection: Connection timed out.

FTP works by having two connections between the client and server.
What you are seeing is, ISTR, the kind of thing that happens when the
FTP client is behind the firewall that doesn't allow the server to make
the return connection.
This points to a firewall issue as well. Does Edgy have a firewall by default? Or is there some kind of security feature that would block the connection that Edgy has and Breezy didn't?

---

### Post by tassou on 2006-11-04
Hi,

thank you Catlett, that is all good points, in particular the one of the possible firewall in Edgy, but after a quick look I did not find anything like that.
Another surprising point is that is occurs in the middle of the synchro process, with no predictable pattern.
Has anyone encoutered such a connection drop in any type of transfert using a tcp-based protocol ?

Thanks

---


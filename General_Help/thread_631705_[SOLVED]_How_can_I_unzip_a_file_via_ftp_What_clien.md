---
title: "[SOLVED] How can I unzip a file via ftp? What client should I use?"
date: 2007-12-04
forum: General Help
---

### Post by thenetduck on 2007-12-04
HI 

I don't know how to unzip a file via ftp on my server. I was wondering if ....

A) someone knows how to do this with gFTP or FireFTP 

B) somone knows of an ftp client that has this feature

Thanks

The Net Duck

---

### Post by davidgarcin on 2007-12-04
Sorry, that's not possible.  Unzipping a file would require some kind of shell access to the FTP host, which no FTP client can give you.  FTP only does what it describes, i.e. transferring files.  You could just grab the file from the server, unzip it, and transfer back though.

That said, if you do have shell access through ssh (or something similar), all you have to do is run "unzip /path/to/theFile".  The syntax may vary depending on what type of host you are connecting to.

-Dave

---

### Post by thenetduck on 2007-12-04
OH duh! I can ssh in .. Thank you very much Dave

The Net Duck

---


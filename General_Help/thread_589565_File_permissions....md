---
title: "File permissions..."
date: 2007-10-24
forum: General Help
---

### Post by noodlemonkeh on 2007-10-24
Hi there!

I'm using Hellanzb to download from usenet, and have the Hellaworld web interface for it. I have changed the interface so that I can upload .NZB files to the page and it puts them in the right folder to start the download, but I get this error:

ERROR: Unable to read NZB file: /home/noodle/nzb/daemon.queue/mysql.nzb
ERROR: Unable to move invalid NZB: /home/noodle/nzb/daemon.queue/mysql.nzb out of the way

I checked the permissions of the file and I get this:
-rw------- 1 www-data www-data 4927 2007-10-24 12:36 mysql.nzb

I have found out how to change the permissions using chmod, but I have to do that manually. 

What I want is to allow all files put in this directory to be able to be read and moved by Hellanzb.

Any ideas?

---

### Post by vanadium on 2007-10-24
"all files put in that directory": When put there usng normal copy or move operations, the file just keeps its permissions. If another mechanism is involved, then the file might be given the permissions as determined by the permissions of the directory. Thus, you might need to make sure that user Hellanzb has rights.

What could work is to change the group permissions of the daemon.queue directory to read-write. Then, you could add user Hellanzb to the www-data group, which would give him the right to read/write in that directory (and move the files owned by the www-data group).

Otherwise, there is a mechanism of ACLs, access control lists, that allows finer control over permissions, but I am not familiar with that.

---


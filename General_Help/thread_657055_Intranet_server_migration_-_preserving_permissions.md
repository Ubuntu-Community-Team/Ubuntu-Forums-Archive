---
title: "Intranet server migration - preserving permissions with FTP"
date: 2008-01-03
forum: General Help
---

### Post by transistor on 2008-01-03
I am replacing my old Ubuntu 5.10 intranet server with a new box and 7.10. I have the server and FTP working and now need to transfer everything under /var/www/, the cron jobs and mySQL databases.

When I ftp from my old box to the new box the permissions, user and group are wrong. (User and Group are set to 0 and file permissions are more restrictive on the new box.)

What's the best procedure? Should I replicate the few users on the new box?

Many thanks.

---

### Post by transistor on 2008-01-03
Here's how I did it:

Tar the files on the old box.
FTP them to the root of the new box.
Untar them on the new box.

---


---
title: "FTP Server without Login from Browser"
date: 2007-11-16
forum: General Help
---

### Post by KawiRider on 2007-11-16
Hello all,

I'm trying to set up an FTP server on our new server where I work,  Ideally, we'd like to replicate exactly how the old FTP server was configured (which was set up years before I came to work here).  Basically, we'd like our "outbox" to be openly accessible for downloading to anyone, anywhere without needing a login.  Essentially what I mean is, when some one types

[ftp://ourservername.university.edu](ftp://ourservername.university.edu)  (not a real url)

into their web browser, we want them to see

inbox
lost+found
outbox

where they are free to browse the outbox and its subdirectories without having to login.

To elaborate, I have a partition mounted at /var/ftp.  Inside this directory will be inbox, lost+found, and outbox.  Of course, I'd like to configure the FTP server so that /var/ftp is the "root" directory of the ftp server so that only FTP files are accessible from the internet.  In /var/ftp/outbox, a number of subdirectories will exist, each one corresponding to a different user we have set up on the server (i.e. /var/ftp/outbox/user1, /var/ftp/outbox/user2, etc).  Each user directory should have write permission only for the user that owns it.  We'd like these users to be able to login from a Windows FTP client (such as WinSCP) and be able to upload their files to their FTP directories remotely.

I've tried using proftpd and vsftpd, but I'm just not sure how to configure them to do what I have described.  If anyone could help by providing assistance or links to guides, etc. it would be greatly appreciated.

Thank You.

---

### Post by KawiRider on 2007-11-19
I looked into a bit more and tried to configure proftpd for anonymous access but that didn't seem to work either.  Perhaps I configured it incorrectly?  Any help would be appreciated.

---


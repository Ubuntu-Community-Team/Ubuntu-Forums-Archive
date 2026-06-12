---
title: "Samba Permissions not working!"
date: 2005-03-31
forum: General Help
---

### Post by phill on 2005-03-31
I have three machine mounting a samba share on a debian server running 3.0.11 (just updated as 3.0.10 has some serious problems).  There's an XP box, Warty  and Hoary.  Both Ubunutu machines have the following entry in fstab:
\\Server\Documents /home/phill/Documents smbfs user,uid=nobody,gid=phill,guest  0  0

and both are running smbfs and samba-common 3.0.7-1-ubuntu6 (just downgraded Hoary to it).  The Hoary machine has a 2.6.5 kernel while Warty uses 2.4.21.

Basically with Warty and even windows I get the correct file permissions from my shared drive, e.g.
-rwxr-xr-x  1 nobody phill 11K 2005-02-17 18:14 documents.sxw
-r-xr-xr-x  1 nobody phill 16K 2005-01-18 15:34 timesheet.sxw   (this file is read only as it is on the server)

Under Hoary I just get:
-rwxr-xr-x  1 nobody phill 11K 2005-02-17 18:14 documents.sxw
-rwxr-xr-x  1 nobody phill 16K 2005-01-18 15:34 timesheet.sxw
i.e. write access for all files regardless (of course this write access fails but it means that docs don't come up as read only)

The user gets rwx permissions on every file regardless of what it says on the server.  This doesn't happen under Warty nor the windows PC, they both display the properties correctly.

Can anyone explain this / confirm it / point me to the solution?  I downgraded smbfs and rebooted to rule out it being down to 3.0.10 but no luck.  Does that mean there's something weird in the kernel?

Thanks...

---

### Post by jdodson on 2005-03-31
do not cross post!

---

### Post by phill on 2005-04-01
Sorry, I didn't realise I was in the Warty section when I first posted and couldn't see how to delete the thread.  This does belong here under Hoary as it works fine under Warty...

---

### Post by phill on 2005-04-01
Further to my original report it seems that using Nautilus to browse to (Places) Network Places and into the share the user permissions are correct.  When I try to remount with only the option "defaults" it still comes back saying rwx permissions for the user on all files...    :-({|= 

Nautilus is built with a separate samba code and doesn't rely (AFAIK) on smbfs which still hints at a kernel / smbfs problem...

Any help please?

---

### Post by phill on 2005-04-04
Well, I got it solved but I'm disappointed nobody here could offer the straightforward answer :-(

I'm quite an experienced debian user and Ubuntu was the first time I switched to a 2.6 kernel.  The basic problem is that "smbfs" should no longer be the type for a samba share, it should be "cifs".  Change my /etc/fstab entries and everything works as expected (although I did have to "modprobe cifs" first).

If anyone else has samba mounting problems just make sure you are using cifs with the 2.6 (Hoary) kernel...

---


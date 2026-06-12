---
title: "nfs server problem"
date: 2005-08-09
forum: General Help
---

### Post by mira-ceti on 2005-08-09
Hi 

I am trying to use my Hoary box as an NFS server and connect my Suse 9.2 box to the exported share.  I can see and read the exported share on the Hoary box from the Suse box but I cannot write to the share from the Suse box.  
I have set the permissions on the share to 777 and still cannot write to the share.  I suspect that I need to change the uid and gid on the exported folder to match the uid and gid on the Suse box. 

My questions are 

1) is this likely to be the problem and if so 

2) How do I change the uid and gid on a folder in Ubuntu ?

Any suggestions would be greatly appreciated.

---

### Post by EmmEff on 2005-08-09
If the permissions on the share are 777 (rwxrwxrwx) then it's not an issue of mismatched UIDs/GIDs.

I don't know anything about SuSE but ensure the mount is actually mounting "rw" (read/write) and if it is, ensure the share is exported "rw".

Failing that, grab Ethereal (network traffic analyzer), "trace" the NFS traffic and see if you can see anything obvious.

---

### Post by mira-ceti on 2005-08-10
Thanks for the help, very much appreciated  :)

---

### Post by EmmEff on 2005-08-10
No problem.  Were you able to solve the problem?  If so, what was it?

---


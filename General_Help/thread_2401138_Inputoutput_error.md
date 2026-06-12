---
title: "Input/output error"
date: 2018-09-13
forum: General Help
---

### Post by albert41 on 2018-09-13
Hi,
I was wondering if someone else has had the same issue, recently realized every now and then im getting this error currently using restic to backup my smb shares

         
            ```
scan: lstat /media/servers/zeus/shares: input/output error
```

not sure if its restic or the CIFS, i mount the SMB share on ubuntu  server with restic. Then restic copies that smb share to another folder  internally of the ubuntu server, out of 1 week maybe 1 time i get this  error which therefore does not do the backup. maybe someone else has had  this issue before? I was looking up the error but could not get a real  answer to solve this.
 Thank you

---

### Post by wildmanne39 on 2018-09-13
Hello, input/output errors usually means the drive is failing, it would be a good idea to check your drive to see if that is the case.

---


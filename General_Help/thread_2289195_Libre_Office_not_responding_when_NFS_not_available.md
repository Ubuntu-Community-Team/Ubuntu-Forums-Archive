---
title: "Libre Office not responding when NFS not available (recent docs)"
date: 2015-08-02
forum: General Help
---

### Post by tschlaeppi on 2015-08-02
Hi, 

I' using Ubuntu 15.04, have mounted a NFS Share (Synology Diskstation DS212j) where some documents are stored.
The NFS share is mounted using an entry in my fstab:
```
MyIP:/volume1/nas /mnt/nas nfs auto,user,defaults,rsize=32768,wsize=32768,tcp,intr,soft 0 0
```

Some of the documents are in my "Recent Documents" list in Libre Office 4.4.2.2.

When i boot up my machine, the NAS is available and the documents are listet under "Recent Documents".
When i'm loosing my wlan connection, or the nas shuts down, libre office hangs an it is not responding (also while writing on a new document which is not stored on the nas).
The program resumes to work, when the connection to the nas is established again.

I think, that LibreOffice is hanging because the Recent Documents which are stored on the NAS aren't available, when the connection is lost.

Are there any options in LibreOffice or in fstab which prevents LibreOffice from hanging?

Thanks, 

Thomas

---

### Post by SeijiSensei on 2015-08-02
Probably it hangs when LO tries to save interim copies of the document.

Why not copy the documents locally, work on them there, then copy them back to the NFS server?

---

### Post by tschlaeppi on 2015-08-02
Unfortunatley, LO hangs also if i work on a locally stored document and loosing the connection to my nas.
So, copying documents to local is no option.

---


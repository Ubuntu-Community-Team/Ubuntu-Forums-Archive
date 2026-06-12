---
title: "Connectiong To Windows 2003 Network Shares Problems"
date: 2007-04-14
forum: General Help
---

### Post by MK_MIke on 2007-04-14
Hello,

I'm attempting mount a network share on my ubuntu(eggy) box so i can listen to my music and access some other documents, i have read the ubuntu guide about it and i have tryed conencting to the share with the following command ' mount //10.10.0.5/MKDocs /media/mkdocs/ -o username=mknights,password=xxxxxxxx,dmask=777,fmask=777 ' but when i do i get the folowing error.

'cli_negprot: SMB signing is mandatory and we have disabled it.
7057: protocol negotiation failed
SMB connection failed'

I really would like to my music!!!!!

Has any one got any ideas?

---

### Post by pointone on 2007-04-14
Try editing your /etc/smb.conf and add the lines:

```
client signing = yes
server signing = yes
```

under the [global] section.

---


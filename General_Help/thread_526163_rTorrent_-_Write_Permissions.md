---
title: "rTorrent - Write Permissions"
date: 2007-08-15
forum: General Help
---

### Post by oxygen on 2007-08-15
Hi all,

I'm using rTorrent to download files into a folder which is shared via samba. However rTorrent is creating the downloaded files without write attributes for group or others. Thus I can't get delete (or modify) the downloaded files.

Should I be changing something in rTorrent (to make it create files with different permissions), changing the user that it runs as or maybe change some settings in the samba configuration.

Thanks in advance!

---

### Post by renzokuken on 2007-08-15
its a samba configuration problem, could you post your smb.conf along with any info on which folders you want access (read/write) to.

---


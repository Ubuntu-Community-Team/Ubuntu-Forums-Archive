---
title: "rsync error 'file havanished'"
date: 2007-10-23
forum: General Help
---

### Post by IcarusR on 2007-10-23
I have used rsync to backup my 43Gb mp3 collection to a NAS drive before upgrading HDDs. When I restore files using this code> rsync -avu /pad/music/ /music I get the following > file has vanished: "/home/andy/pad/music/ACDC/Highway To Hell/Highway To Hell.m3u"

sent 279886 bytes  received 48 bytes  20735.85 bytes/sec
total size is 46220623549  speedup is 165112.57
rsync warning: some files vanished before they could be transferred (code 24) at main.c(977) [sender=2.6.9]
 Origionally 105 files had 'vanished', but with repeatedly running the command I have got all bar one restored.
Has anyone else had this problem & does anyone know why it happens ??
Is there any way to get rsync to log these 'vanished' files ?

Thanks Icarus

---


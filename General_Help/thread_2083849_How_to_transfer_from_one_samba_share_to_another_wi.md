---
title: "How to transfer from one samba share to another without involving windows"
date: 2012-11-13
forum: General Help
---

### Post by eternal3000 on 2012-11-13
Hello,

 I currently have Ubuntu Server (latest release) installed on a media server  with 4 (3TB WD green) hot swap drives.  I only use the server to view and download media (downloads through uTorrent server).  Currently I download all the media to one of the 4 drives and then transfer the completed files to the other drives. This transfer is done in Windows 7 as I made the drives samba shares to work with my various devices (WDTV, Boxee). However when I drag and drop the files from one Samba share to the next it is essentially downloading the file to my computer and then sending it over to the new drive (rather than recognizing they are both on the same computer and transferring it directly) which can take quite a bit of time. 

This all said, is there a program (like FXP) or option I can use to transfer the files faster? I realize I could do it manually through ssh but am trying to avoid that given I can't just copy all due to the different media types needing to go into different samba shares.

Regards and thanks for any assistance available!

Eternal3000

---

### Post by audiomick on 2012-11-13
Presumably it is Ubuntu server with no GUI? And the drives in question are all always mounted in the server?

I think you need to look at the commands cp and mv.

Do
```
man cp
```

and 
```
man mv
```

to see the manual pages for these commands.

---

### Post by edwardecl on 2012-11-13
That's exactly what he did not want to do...

But no there is no way of transferring from one drive to another locally via samba from presumably another computer.

Would be great if you could... I have the same issue... you could log in via ssh and find the dir and mv it... but that's a lot of hassle.

---


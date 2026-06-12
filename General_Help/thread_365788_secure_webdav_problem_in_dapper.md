---
title: "secure webdav problem in dapper"
date: 2007-02-20
forum: General Help
---

### Post by treesurf on 2007-02-20
Aloha all,

I am having a problem connecting to a secure webdav server using the "Connect to server" function in Dapper.  I am able to create the connection on the desktop.  When I open it creates not one, but almost a dozen password windows.  I enter my password in the first one, and it does connect, but then there are still the other ten or so password windows that float in front of everything on the desktop and are extremely stubborn about closing.  If I do manage to get them all closed (seems like I have to cancel them in the correct order) and I try to click on a directory in the server browser window it does it all over again.  

I can connect to this same server without any problems on both Windows and MacOSX computers so I'm assuming the problem must be with Ubuntu.

Any help would be appreciated on some tips to getting this working correctly.  I did a search on the forums, but haven't found any mention of a similar problem.

Thanks

---

### Post by RikoW on 2007-02-20
I actually use the davfs2 file system to mount webdav folders from the command line. Then you can just access them like a normal linux directory either from the command line or via nautitilus.

See for example this post

[http://ubuntuforums.org/showpost.php?p=2116697&postcount=12]("http://ubuntuforums.org/showpost.php?p=2116697&postcount=12")

on how to set-up and use davfs.

Cheers,

               Riko

---

### Post by treesurf on 2007-02-21
Thanks Riko, I'll give that a shot.

---


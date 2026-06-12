---
title: "Samba share problem"
date: 2008-05-05
forum: General Help
---

### Post by Go_Bucks on 2008-05-05
I am suddenly having a problem with Samba shares and permissions since I upgraded to 8.04, and this problem exists whether the share is on my Ubuntu server or the Windows server at the office. Here, I will use the windows server as an example:

-I can access files on the windows server with no problem.
-I can open existing files that reside on the windows server, edit them, and save them with no problem.
-If I create NEW files on my ubuntu laptop and save them to the windows server, I can NOT edit them directly from the server. I am told I do not have permission. I can edit those files on Windows, however.
-This is true even if I make certain that the folders and files being transferred to the server are set to allow read and write access for all.

Any help on this would be appreciated.

---

### Post by Go_Bucks on 2008-05-05
bump  ... I have been working on this for four hours and nothing I can find is working

---

### Post by Go_Bucks on 2008-05-05
At the moment, the appropriate line in my fstab looks like this:

//5.108.30.228/e-nrc_graphics/ /home/marcus/NRC auto rw,user,umask=000 0 0

Which obviously is not correct. I arrived at this after going through several different sites describing ftsab setup. None of them work. I have read/write access to folders, but read only access to files.

---

### Post by Go_Bucks on 2008-05-05
Tried with the following:

//5.108.30.228/e-nrc_graphics/ /home/marcus/NRC cifs file_mode=0777,dir_mode=0777 0 0

still not working...

---

### Post by iswa on 2008-05-06
> **Go_Bucks said:**
> Tried with the following:
 
//5.108.30.228/e-nrc_graphics/ /home/marcus/NRC cifs file_mode=0777,dir_mode=0777 0 0
 
still not working...
 
 
I mount my office network's shares using a script as follows:
 
 
```
sudo mount -t cifs "//<server/share>" <mount point> -o username="<username>",password='<password>',iocharset=utf8,file_mode=0777,dir_mode=0777 -o setuids
```
 
 
I think the 'setuids' may be what you are missing - I had a similar problem to yourself and this fixed it.
 
 
Hope this helps.

---

### Post by Go_Bucks on 2008-05-06
I managed to fix it using "no perms" today. Thanks for the reply.

---

### Post by Blaque on 2008-05-06
I have the same problem. I am looking at the file permissions as they are created and its not following the the create or directory mask set in samba.

The server is CentOS 5 and the client is Ubuntu 8.04. I tried the "no perms" option given above but the file permissions were even further off than the mask at that point.

---

### Post by Go_Bucks on 2008-05-07
You know, in researching this issue it appeared that a lot of people starting having permissions issues in Hardy that didn't exist in previous ubuntu versions.

---

### Post by Blaque on 2008-05-07
I just started researching and this was the only discussion I had found so far.

I figured there must have been a samba update with 8.04 and it didn't like something in my rush job setup of mounts. Could you list some of the other discussions you have found?

---

### Post by Go_Bucks on 2008-05-07
Didn't keep them... sorry. I used google and yahoo, spending about six hours on the problem yesterday.

---

### Post by wmf on 2008-05-09
Well, I used the ```
sudo mount -t cifs "//<server/share>" <mount point> -o username="<username>",password='<password>',iocharset=utf8,file_mode=0777,dir_mode=0777 -o setuids
```and it seemed to work fine. Now, however, I find that it is a one way journey only. I can download files off the share to the local Hardy machine, but I can upload any files to the share. Although it fails with a generic "I/O Error", my guess is that something to do with perms, but again, I see no way to authenticate beyond the login/password in the mount command.

---


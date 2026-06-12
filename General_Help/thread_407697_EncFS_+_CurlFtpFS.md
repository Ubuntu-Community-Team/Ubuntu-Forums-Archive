---
title: "EncFS + CurlFtpFS"
date: 2007-04-12
forum: General Help
---

### Post by kathan on 2007-04-12
Hi,

I was trying to use EncFs on top of CurlFtpFS but it didn't work. 
1) I've mounted a ftp site in ~/remote with CurlFtpFS. It works fine.
2) I've tried to mount ~/remote/encrypted to ~/storage with this commmand :
   encfs /home/alain/remote/encrypted /home/alain/storage/
   but it doesn't work. Even as root.
The command doesn't fail but I can't accede to ~/storage. (permission denied)

---


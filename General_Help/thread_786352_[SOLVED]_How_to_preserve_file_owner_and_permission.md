---
title: "[SOLVED] How to preserve file owner and permissions after FTP file?"
date: 2008-05-08
forum: General Help
---

### Post by abcuser on 2008-05-08
Hi,
I would like to FTP file from test computer to production computer. But every time I use FTP owner of file get changed and also permissions of file. So root has read/write permissions (like chmod 600). I would like to FTP file and preserve owner and permissions. Is this possible?
Regards,
Abcuser

---

### Post by Rocket2DMn on 2008-05-08
As far as I know, FTP does not preserve file permissions when you transfer (though sftp might).  When you download it saves to your computer with your username (or the username that is running the ftp client) and when you upload, files are owned by the username that you logged in with.  You can set permissions by right clicking the file(s) or through SSH to the ftp host.  You can chmod/chown either way.  You may also be able to tell your client to set specific default permissions, but this would vary from client to client (if it's even possible).

---

### Post by abcuser on 2008-05-10
> **Rocket2DMn said:**
> ...or the username that is running the ftp client...Thanks a lot. I have asked FTP administrator to give ftp-download-upload rights to my username. Now I have permissions set for my username.
Thanks.

---


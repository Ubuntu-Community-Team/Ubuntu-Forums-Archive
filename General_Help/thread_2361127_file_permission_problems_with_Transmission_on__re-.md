---
title: "file permission problems with Transmission on  re-installed system"
date: 2017-05-12
forum: General Help
---

### Post by checoimg on 2017-05-12
I'm trying to download the Xubuntu torrent and I'm getting a ```
Error: Permission Denied (Path/to/iso)
```.

I tried moving me to the Users group and my Home folder files too but I got the same error. I re-downloaded the torrent and got the same.

Transmission can start the download normally but then gives me the error.

This is a re-installed system with a separate Home HDD for the HOME folder, the purpose has been to do a reinstall without losing files.

My file permission never gave errors in the past using this re-installation process so I'm lost on this one.

---

### Post by TheFu on 2017-05-12
I don't know anything about transmission, but I do know file and directory permissions.
The process owner determines which userid is being used for file and directory permissions.  If your userid is running transmission, then the only places where files can be written are places that your userid has write access.  

If you are running transmission under a different account (or as a daemon), then where ever the files are being stored (attempted to be stored) must allow that other userid write access.

So, if you provide the output from '**id**' and the **ls -al** on the directory where you are trying to save the files, I can tell you the fix.  Please use correct paths which begin from / to prevent confusion.

---

### Post by checoimg on 2017-05-14
Thank you very much for the response, next time I'll wait more for a response.

I ended up by making a clean install and moving all Home files to another folder during installation and was able to download the ISO, here's my output.

```
ls -la
drwxr-xr-x 50 userx userx      12288 may 13 23:06 Downloads

id
uid=1000(userx) gid=1000(userx) groups=1000(userx),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),129(sambashare)
```

---


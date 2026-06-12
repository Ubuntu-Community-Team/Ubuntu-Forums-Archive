---
title: "[Dum question] launch stuff on init"
date: 2013-01-08
forum: General Help
---

### Post by heWhoWearsAshes on 2013-01-08
Could someone give me a link, or explain how it works, to anything that has to do with having stuff start up at init. I wanna make my server-y comp. start nfs and ftp when it starts up.

---

### Post by rubylaser on 2013-01-08
If you are using the NFS and FTP packages from the repositories (and have installed them), they will come with upstart scripts that are already setup to start themselves automatically.

You can check if NFS is running like this.

```
ps aux | grep nfs
```

And it's init script is at /etc/init.d/nfs-kernel-server

---


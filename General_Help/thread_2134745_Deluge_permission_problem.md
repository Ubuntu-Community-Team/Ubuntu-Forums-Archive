---
title: "Deluge permission problem"
date: 2013-04-12
forum: General Help
---

### Post by karnalta on 2013-04-12
Hi,

I have installed deluged and deluge-web on my Ubuntu 12.04 server by following [this guide]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript/Ubuntu%2011.04%2B%20%28Upstart%20Job%29").

All work fine, except that when I try to change the download destination directory to /mnt/raid5/torrents, I always get "Permission denied: /mnt/raid5/...." when I download a torrent.

I have tried to do :

```
chown -R deluge:deluge /mnt/raid5/torrents
chmod -R 777 /mnt/raid5/torrents

```

But I still have the same error, I don't understand why it can"t have access with a chmod 777 on the directory ..

Thank for your help.

---

### Post by rnerwein on 2013-04-12
> **karnalta said:**
> Hi,

I have installed deluged and deluge-web on my Ubuntu 12.04 server by following [this guide]("http://dev.deluge-torrent.org/wiki/UserGuide/InitScript/Ubuntu%2011.04%2B%20%28Upstart%20Job%29").

All work fine, except that when I try to change the download destination directory to /mnt/raid5/torrents, I always get "Permission denied: /mnt/raid5/...." when I download a torrent.

I have tried to do :

```
chown -R deluge:deluge /mnt/raid5/torrents
chmod -R 777 /mnt/raid5/torrents

```

But I still have the same error, I don't understand why it can"t have access with a chmod 777 on the directory ..

Thank for your help.
good morning
i can't help you with your problem, but i can tell you ! never use: chmod -R 777 bla_blu_bla this never make sense !!!!!
ciao

---

### Post by karnalta on 2013-04-12
I know I should not use chmod 777, but it's only for testing purpose.

I trying to understand how deluge user can't access to a directory who is chmoded at 777.

---

### Post by Vaphell on 2013-04-12
assuming /mnt/raid/torrents is mounted, what are the mount permissions?
what does* ls -la /mnt/raid/torrents* say?

---


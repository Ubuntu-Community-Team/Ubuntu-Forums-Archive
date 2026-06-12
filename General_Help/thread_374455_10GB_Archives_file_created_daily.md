---
title: "10GB Archives file created daily"
date: 2007-03-02
forum: General Help
---

### Post by Smokeymcpawt on 2007-03-02
Daily, between 7AM-2:45PM a 10gb file is being made in /var/archives. I have no idea why it is being created, or how. Any idea of what program writes to that location?

---

### Post by taurus on 2007-03-02
Look in /etc/cron.daily to see if you have a daily backup running in there.

```
ls  -ls  /etc/cron.daily
```

---

### Post by kpkeerthi on 2007-03-02
```

du -sh /var/archives

```

Is it 10 GB.. really?

---

### Post by Smokeymcpawt on 2007-03-02
4 -rwxr-xr-x 1 root root  111 2007-02-28 22:19 backup-manager
Looks like it would be the culprit, how do i remove that cron?

> **kpkeerthi said:**
> ```

du -sh /var/archives

```

Is it 10 GB.. really?
A little more actually.

---

### Post by taurus on 2007-03-02
Instead of removing it, just move to root's $HOME in case you need to use it later.

```
sudo mv /etc/cron.daily/backup-manager  /root
```
Then, reboot.

---

### Post by Smokeymcpawt on 2007-03-03
Thanks alot, It made another one before I had the chance to do that.


> 
jared@jareds:/var/archives$ ls -l -h
total 13G
-rw------- 1 root root  61 2007-03-03 07:43 jareds-20070303.md5
-rw------- 1 root root 13G 2007-03-03 08:20 jareds-home.20070303.tar.gz


It's about 12.8GB :)

---

### Post by taurus on 2007-03-03
Well, just remove them.

```
cd /var/archives
sudo rm jareds*
```

---

### Post by Smokeymcpawt on 2007-03-03
> **taurus said:**
> Well, just remove them.

```
cd /var/archives
sudo rm jareds*
```

Already did. :)

---


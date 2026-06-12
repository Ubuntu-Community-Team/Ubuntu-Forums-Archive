---
title: "how to link one folder to another folder"
date: 2016-11-15
forum: General Help
---

### Post by stupidquestion on 2016-11-15
I'm trying to point one folder to another folder by using a symbolic link.
My target files are located at: /mnt/varwww/
I want the following folder to point there: /var/www/html/
(That is, when I type "ls /var/www/html", I want to see the contents of /mnt/varwww/)

I did "sudo ln -s /mnt/varwww/ /var/www/html/", but that creates a link called "varwww" under /var/www/html/, which is not exactly what I want.

Then I tried "sudo ln -s /mnt/varwww/* /var/www/html/", which seems to point to the files ok, but the contents of the original folder still remained.

Is there a way to do what I want without deleting the original folder's contents?

---

### Post by kpatz on 2016-11-15
Rename the /var/www/html directory to something else like html_original:```
sudo mv /var/www/html /var/www/html_original
```

Then create the symlink:```
sudo ln -s /mnt/varwww /var/www/html
```

If you want the files/directories that were in /var/www/html (now /var/www/html_original if you renamed it as above) still accessible under that path, copy/move them to /mnt/varwww.

You should also change the ownership and permissions of /mnt/varwww to be the same as the original /var/www/html using chown and chmod.  On my system it's root:root and 0755:
```

sudo chown root:root /mnt/varwww
sudo chmod 755 /mnt/varwww

```

---

### Post by stupidquestion on 2016-11-15
> **kpatz said:**
> Rename the /var/www/html directory to something else like html_original:```
sudo mv /var/www/html /var/www/html_original
```

Then create the symlink:```
sudo ln -s /mnt/varwww /var/www/html
```

Thanks, that was straight forward.

> You should also change the ownership and permissions of /mnt/varwww to be the same as the original /var/www/html using chown and chmod.  On my system it's root:root and 0755:
```

sudo chown root:root /mnt/varwww
sudo chmod 755 /mnt/varwww

```

Hmm my permissions didn't change. I did take ownership but I think it was already root:root before. Could it because that folder (/mnt/varwww) is special because it was a shared folder (from the host) mounted by VirtualBox?

Update:
I remembered to add my username to the vboxsf group:
```
sudo adduser USERNAME vboxsf
```
Then I could change the permissions of the target (/mnt/varwww).

The link "/var/www/html" still has permission 777 which can't be changed though.

---


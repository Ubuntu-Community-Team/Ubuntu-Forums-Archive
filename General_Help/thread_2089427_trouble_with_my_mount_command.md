---
title: "trouble with my mount command"
date: 2012-11-29
forum: General Help
---

### Post by Dragonbite on 2012-11-29
I have an networked hard drive (purchased one, not a linux-running system which would be a lot easier).

If I run the mount command manually, it mounts with no problem```
sudo mount //192.168.0.105/"goflex home backup" /media/goflex_home/ -t smbfs -o username=<username>,password=<password>
```

When I try and mount it in the /etc/fstab it won't mount saying ```
[mntent]: line 27 in /etc/fstab is bad
```

---

### Post by pkadeel on 2012-11-29
> **Dragonbite said:**
> I have an networked hard drive (purchased one, not a linux-running system which would be a lot easier).

If I run the mount command manually, it mounts with no problem```
sudo mount //192.168.0.105/"goflex home backup" /media/goflex_home/ -t smbfs -o username=<username>,password=<password>
```When I try and mount it in the /etc/fstab it won't mount saying ```
[mntent]: line 27 in /etc/fstab is bad
```
what is the line 27 in fstab? provide the output of ```
cat /etc/fstab
```

---

### Post by vanadium on 2012-11-29
This may be your solution in /etc/fstab: [http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path](http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path)

You need to represent spaces as \040

---

### Post by Dragonbite on 2012-11-29
> **pkadeel said:**
> what is the line 27 in fstab? 

Sorry about that, I got interrupted before I could look over my post and include the line in /etc/fstab.  Yes, line 27 is the line I am trying to mount.```
//192.168.1.105/"goflex home backup"		/mnt/goflex_home	smbfs	noauto,username=<username>,password=<password>	0	2
```

> **vanadium said:**
> This may be your solution in /etc/fstab: [http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path](http://en.kioskea.net/faq/2287-fstab-adding-spaces-in-the-mount-point-path)

You need to represent spaces as \040

This is helpful.  I changed it with "0/040" mentioned in the article, followed by "/040" and then "\040" and I am getting > mount error(113): No route to host
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


So I guess the next thing to check is mount.cifs

---

### Post by pkadeel on 2012-11-29
> **Dragonbite said:**
> Sorry about that, I got interrupted before I could look over my post and include the line in /etc/fstab.  Yes, line 27 is the line I am trying to mount.```
//192.168.1.105/"goflex home backup"        /mnt/goflex_home    smbfs    noauto,username=<username>,password=<password>    0    2
```

This is helpful.  I changed it with "0/040" mentioned in the article, followed by "/040" and then "\040" and I am getting 

So I guess the next thing to check is mount.cifs
I am not sure but looks like your samba share is not present (connected whatever) when the fstab file is read during startup. Have you tried using the 0 fsck option instead of 2

---

### Post by Dragonbite on 2012-11-30
> **pkadeel said:**
> I am not sure but looks like your samba share is not present (connected whatever) when the fstab file is read during startup. Have you tried using the 0 fsck option instead of 2

I'll give that a try when I get home.  

Funny thing is that when I run "sudo mount -a" or "sudo mount /mnt/goflex_home" it comes back with that error even though I can have nautilus with it open in the background.

And like I said, running the command in the first post, it connects, just not in /etc/fstab.

---

### Post by Cheesemill on 2012-11-30
With nautilus open browsing the share can you post the result of:
```
mount
```

---

### Post by vanadium on 2012-12-01
The reason it does not connect in /etc/fstab may be because the network is not available yet at the time fstab is processed. Add the option _netdev to overcome this.

---

### Post by Cheesemill on 2012-12-01
> **vanadium said:**
> The reason it does not connect in /etc/fstab may be because the network is not available yet at the time fstab is processed. Add the option _netdev to overcome this.
I'm pretty sure this isn't the problem, if you read the OP's post above:
> Funny thing is that when I run "sudo mount -a" or "sudo mount  /mnt/goflex_home" it comes back with that error even though I can have  nautilus with it open in the background.

---


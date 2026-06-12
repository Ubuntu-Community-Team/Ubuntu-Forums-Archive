---
title: "Samba - user cannot create file or directory"
date: 2015-03-31
forum: General Help
---

### Post by croat on 2015-03-31
Hi! I have been struggling with Samba for a few days, looking for every thread that could help me. Unfortunately I have not been able to solve my problem and came here to ask for your help. English is not my native language, so please excuse my mistakes.

I created a directory in /home, with **chmod 755** and **g+s**:

```
drwxrwsr-x 2 root      sharegroup  4096 mars  31 23:54 sharedir
```

We can see in **/etc/group** that croat is in sharegroup:

```
sharegroup:x:1006:croat
```

Now in **smb.conf**:

```
[mydir]
   path = /home/sharedir
   browseable = yes
   guest ok = no
   create mask = 0775
   directory mask = 0775
   valid users = @sharegroup
   write list = @sharegroup
```

I can mount it using:
```
sudo mount -t cifs -o user=croat //192.168.142.20/mydir /mnt/smb/
```

Sadly, I cannot create anything on /mnt/smb. Note that if I do **chown croat:sharegroup sharedir/** or **chown root:croat sharedir/** (server side, of course), I gain writing privileges on the client side. My point is that Samba doesn't seems to recognize me as a member of sharegroup. Also, **force group = sharegroup **doesn't changes anything.

---

### Post by gordintoronto on 2015-04-01
Version of Ubuntu? You did install Samba?

---

### Post by croat on 2015-04-01
> **gordintoronto said:**
> Version of Ubuntu?
All is up to date

> **gordintoronto said:**
>  You did install Samba?
You did read my message? I talked about smb.conf for my server, and I can mount it on my client.

---

### Post by gordintoronto on 2015-04-01
Ubuntu Desktop or Server? 14.04 LTS?

I always just use Nautilus to set up shares, but if you're running Server, that is no help.

---

### Post by croat on 2015-04-01
Server yes. Actually I have KDE on my client so I haven't Nautilus, but it's not relevant as I only used a terminal to set up my samba share and mount it.

---


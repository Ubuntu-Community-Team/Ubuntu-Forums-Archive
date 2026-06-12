---
title: "How do I make a folder accessible to all users?"
date: 2007-04-08
forum: General Help
---

### Post by marqmike2 on 2007-04-08
So, I'm using vsftpd in drapper drake so I could access files on the server while away from home and to share things with friends and such.  But I want to make it easy to add things to the folder, so I have the root folder of the anonymous portion of the ftp server set as /home/ftp (the default of vsftpd).  The only problem is that when I attempt to log on to the server as a user on my system I am unable to upload files.  I thought to try to put the root in /home/mike/ftp but then the anonymous user can't access any additional files.  So I was hoping there was some way to let everyone own the folder, any suggestions?

---

### Post by Swab on 2007-04-08
> **marqmike2 said:**
> So, I'm using vsftpd in drapper drake so I could access files on the server while away from home and to share things with friends and such.  But I want to make it easy to add things to the folder, so I have the root folder of the anonymous portion of the ftp server set as /home/ftp (the default of vsftpd).  The only problem is that when I attempt to log on to the server as a user on my system I am unable to upload files.  I thought to try to put the root in /home/mike/ftp but then the anonymous user can't access any additional files.  So I was hoping there was some way to let everyone own the folder, any suggestions?

Change the permissions on the folder to allow everyone full access.

```
sudo chmod -R 777 /path/to/folder
```

Not sure this is particularly wise... but it should work.

---

### Post by Famicommie on 2007-04-08
I would suggest
sudo chmod 776 /home/mike/ftp
instead of 777, as it prevents people without accounts on your machine from running executable files.

---

### Post by marqmike2 on 2007-04-08
ok, i tried "sudo chmod 776 /home/mike/ftp" and it seemed like it worked, but now the ftp server won't allow anonymous logins.  I tried restarting it, but to no avail.  Sorry, this was a sorta hasty reply, I'll see if I can get to the logfile for the server.

And also, thank you all for such a quick response.

---

### Post by marqmike2 on 2007-04-08
Here is a recent chunk of the log, I don't know if it would be useful, but what the hell.

> Sat Apr  7 22:06:21 2007 [pid 5348] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:06:27 2007 [pid 5350] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:06:33 2007 [pid 5352] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:06:33 2007 [pid 5354] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:06:33 2007 [pid 5353] [ftp] OK LOGIN: Client "192.168.1.117", anon password "anon@"
Sat Apr  7 22:23:56 2007 [pid 5500] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:24:02 2007 [pid 5502] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:24:08 2007 [pid 5504] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:24:13 2007 [pid 5506] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:24:14 2007 [pid 5505] [mike] OK LOGIN: Client "192.168.1.117"
Sat Apr  7 22:29:17 2007 [pid 5543] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:29:17 2007 [pid 5542] [mike] OK LOGIN: Client "192.168.1.117"
Sat Apr  7 22:43:10 2007 [pid 6052] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:43:10 2007 [pid 6051] [mike] OK LOGIN: Client "192.168.1.117"
Sat Apr  7 22:43:19 2007 [pid 6055] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:43:25 2007 [pid 6057] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:43:26 2007 [pid 6059] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:43:32 2007 [pid 6062] CONNECT: Client "192.168.1.117"
Sat Apr  7 22:43:47 2007 [pid 6064] CONNECT: Client "192.168.1.1"
Sun Apr  8 14:49:34 2007 [pid 8860] CONNECT: Client "192.168.1.1"


Also, when I try to FTP via firefox I now get the error "500 OOPS: child died" when I login under mike, and "500 OOPS: vsftpd: refusing to run with writable anonymous root" when I login as no one (anonymous I assume).  On the other hand, when I login under mike in filezilla it works fine, but when I try to login as an anonymous user, it just doesn't connect.

---

### Post by marqmike2 on 2007-04-08
never mind, i figured it out.  I just set the permissions to 755 (which is more along the lines of what I wanted to do).  Thanks for giving me a good start!

---


---
title: "transfering files through ssh port 22.."
date: 2008-03-27
forum: General Help
---

### Post by Mia_tech on 2008-03-27
I have setup a firewall and the only port it has open the inside of network is 22, I connect, and I've been capturing data with tcpdump, but I can not transfer over to my ubuntu machine usually I transfer using winscp, but I wonder if there's a program like that for ubuntu...

thanks

---

### Post by ghostdog74 on 2008-03-27
sftp or scp is what you need

---

### Post by mozetti on 2008-03-27
Or rsync - rsync has a switch that will automatically use ssh to establish the connection. I'm using rsync (must be installed on both machines) to backup files to my WD MyBook World Edition NAS.

---

### Post by OoooMatron on 2008-03-27
This will put a file from the host to the destination

scp -Pport_number file_name login@destination:dest_path

scp -P22 test.zip [email]me@mydomain.com[/email]:/home/me

---

### Post by phrawzty on 2008-03-27
If you'd rather use a graphical tool (instead of scp from the shell), you might like to check out "FileZilla" - it's available in the standard Ubuntu repos.

```
$ apt-cache show filezilla
   ...
```

---

### Post by Oldsoldier2003 on 2008-03-27
> **phrawzty said:**
> If you'd rather use a graphical tool (instead of scp from the shell), you might like to check out "FileZilla" - it's available in the standard Ubuntu repos.

```
$ apt-cache show filezilla
   ...
```

+1 filezilla has the benefit of being cross platform as well making support easier

---


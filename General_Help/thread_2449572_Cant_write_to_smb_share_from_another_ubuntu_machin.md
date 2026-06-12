---
title: "Cant write to smb share from another ubuntu machine"
date: 2020-08-29
forum: General Help
---

### Post by royalflush5 on 2020-08-29
Hello, I'm trying to get some odd stuff working. I have a proxmox host that is running 2 ubuntu vms. One of them is running a samba share, the other is going to run some applications like plex or nginx, in docker containers. I have a pretty barebones samba conf file:

```
[global]
  workgroup = WORKGROUP
  server string = filedumpster
  security = user
  guest ok = yes
  map to guest = Bad Password

  log file = /var/log/samba/%m.log
  max log size = 50
  printcap name = /dev/null
  load printers = no

# Samba Shares

[dataFiles]
  comment = Data share 
  path = /mnt/storage/data
  browseable = yes
  read only = no
  guest ok = yes
  writeable = yes
```

since this is on my home network I'm not too concerned with permissions and restricting who can access what  (for now at least). On a win10 machine I can read and write no problem. On my other ubuntu machine I have the shares mounted in fstab like this:

```
//%ipaddress%/dataFiles /mnt/data    cifs    guest,uid=100,iocharset=utf8    0 0
```


The shares mount without issues, but I can't seem to write to them without getting permission denied errors. Any clue as to what I should change? Thank you

---

### Post by SeijiSensei on 2020-08-29
Look into the "force user" and "force group" directives for the server's smb.conf. These let you specify a Unix user that has full permissions on the share despite the identity of the logged-in user.

---

### Post by royalflush5 on 2020-08-29
interesting, so should I give that user ownership of the share? say i create a user

adduser --system fileuser

should I give filuser ownership of the share directory? then specify force user in smb.conf?

---

### Post by SeijiSensei on 2020-08-29
Yes.  I've only used an ordinary user for this task, though a system user would probably work just as well.

I suggest you set up a separate share in smb.conf with this feature enabled for testing purposes.  Once it works the way you want, you can then apply it to the real shares.

---

### Post by TheFu on 2020-08-30
uid=100
looks wrong.  Usually, the first userid is 1000, not 100.

---

### Post by royalflush5 on 2020-08-31
> **SeijiSensei said:**
> Yes.  I've only used an ordinary user for this task, though a system user would probably work just as well.

I suggest you set up a separate share in smb.conf with this feature enabled for testing purposes.  Once it works the way you want, you can then apply it to the real shares.


> **TheFu said:**
> uid=100
looks wrong.  Usually, the first userid is 1000, not 100.

Thanks, I fixed that, and added the force user flag with the user i previously created:

```
[appsFiles]
  comment = apps, docker
  path = /mnt/storage/apps
  browseable = yes
  read only = no
  guest ok = yes
  writeable = yes
  force user = shareuser
```

fstab on remote pc:
```
//%ipaddr%/appsFiles /mnt/apps      cifs    guest,uid=1000,iocharset=utf8,sec=ntlm  0 0
```

I can write to the share, but only if I run the command with sudo, if I sudo touch /mnt/apps/test I get this output:

```
total 8
drwxr-xr-x 2 root root 4096 Aug 31 15:30 .
drwxr-xr-x 5 root root 4096 Aug 29 14:27 ..
-rw-r--r-- 1 root root    0 Aug 31 15:30 test
```

If I run it with the user I log into the machine with I get a permission denied error. The uid matches the one in fstab as well...

---

### Post by SeijiSensei on 2020-08-31
> If I run it with the user I log into the machine with I get a permission denied error. The uid matches the one in fstab as well... 

Did you create an entry in the smbpasswd file?

```
sudo smbpasswd -a username
```

You'll be prompted to enter a password.  Use the username associated with account 1000 above.  See if that fixes the permission denied error.  You probably want to use a "credentials" file if you have both a user and password.  I think you'll need to use the username on the server in the file, not the uid.  See [https://linux.die.net/man/8/mount.cifs](https://linux.die.net/man/8/mount.cifs) for details.  Have root own the credentials file with 600 permissions for security.

Make sure the cifs-utils package is installed with
```
sudo apt install cifs-utils
```

There's a command-line client, smbclient, that will let you connect to a Samba server. I believe it comes with default Ubuntu, but if not, you can install it with
```
sudo apt install smbclient
```
For usage, see the man page at [https://linux.die.net/man/1/smbclient](https://linux.die.net/man/1/smbclient).

---

### Post by Morbius1 on 2020-09-01
Which ubuntu machine is running this:
[ATTACH=CONFIG]286851[/ATTACH]
The client or the server?

The reason I ask is the only way this line on the client:
> //%ipaddr%/appsFiles /mnt/apps      cifs    guest,uid=1000,iocharset=utf8,sec=ntlm  0 0
Can produce **drwxr-xr-x 2 root root** permissions on the mount point is if the share failed to mount.

That will happen if the server is running 11 and the client is running 20. It will happen in reverse as well.

If the client to this ancient server is running with a Linux Kernel after 4.12 you need to specify the smb1 dialect in your fstab statement used back then: **vers=1.0 **

That would make it consistent using **sec=ntlm. **Otherwise that sec setting makes no sense. It's incompatible with modern versions of Ubuntu.

---

### Post by royalflush5 on 2020-09-02
> **SeijiSensei said:**
> Did you create an entry in the smbpasswd file?

```
sudo smbpasswd -a username
```

You'll be prompted to enter a password.  Use the username associated with account 1000 above.  See if that fixes the permission denied error.  You probably want to use a "credentials" file if you have both a user and password.  I think you'll need to use the username on the server in the file, not the uid.  See [https://linux.die.net/man/8/mount.cifs](https://linux.die.net/man/8/mount.cifs) for details.  Have root own the credentials file with 600 permissions for security.


got it, this got it working. Make the creds file and used that. now i can work on it no problem. Thanks!

> **Morbius1 said:**
> Which ubuntu machine is running this:
[ATTACH=CONFIG]286851[/ATTACH]
The client or the server?

The reason I ask is the only way this line on the client:

Can produce **drwxr-xr-x 2 root root** permissions on the mount point is if the share failed to mount.

That will happen if the server is running 11 and the client is running 20. It will happen in reverse as well.

If the client to this ancient server is running with a Linux Kernel after 4.12 you need to specify the smb1 dialect in your fstab statement used back then: **vers=1.0 **

That would make it consistent using **sec=ntlm. **Otherwise that sec setting makes no sense. It's incompatible with modern versions of Ubuntu.

Ooohh that is a relic from when I joined. My bad, I forgot to mention that these are both fresh 20.04 machines. I removed the ntlm line and added the credential file as suggested above and i am in business. Thank you both for your help

---

### Post by SeijiSensei on 2020-09-03
> **royalflush5 said:**
> got it, this got it working. Make the creds file and used that. now i can work on it no problem. Thanks!
You're welcome.

---


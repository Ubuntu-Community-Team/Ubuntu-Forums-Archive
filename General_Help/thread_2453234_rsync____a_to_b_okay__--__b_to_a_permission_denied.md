---
title: "rsync    a to b okay  -/-  b to a permission denied"
date: 2020-11-05
forum: General Help
---

### Post by Frank P on 2020-11-05
2 ubuntu 18.04LTS servers / user id & password same on both servers / owners. groups, permissions identical on both servers

server-a to server-b: push & pull - works file
server-b to server-a: permission denied

any suggestions as to what else I can look for
Thanks
Frank

---

### Post by TheFu on 2020-11-05
File systems on both sides?
Matching passwords doesn't matter to rsync.  Do you have ssh-keys setup between the systems in each direction? On Linux, that's just 2 commands, usually.
Firewall?
DNS or other name resolution?  ssh can be picky, if configured to be picky.  If the hostname doesn't answer exactly the same as the DNS, forgetaboutit.
Does **ssh -vvvv** b --> a work?

Can you show the exact rsync commands?

---

### Post by Frank P on 2020-11-05
no firewall active
using static ips
```

ssh -vvvv laozi@192.168.1.87

```
too much output to list but it ssh's to 192.168.1.87

```

ssh -vvvv laozi@192.168.1.89

```
too much output to list but it ssh's to 192.168.1.89
```

rsync /home/laozi/scripts/transfer_out laozi@192.168.1.87/home/laozi/transfer_in

```
seems to ssh okay but skips directory. I'll do some further checking
```

rsync /home/laozi/transfer_out/ laozi@192.168.1.89:/home/laozi/transfer_in

```
this seems to ssh okay too but skips directory. 
since the ssh worked I'll recheck permissions etc.
Thanks

---

### Post by ActionParsnip on 2020-11-05
I suggest making a backup account and putting the account in the group of the user name's data you want to backup. Use SSH keys as usual

---

### Post by Frank P on 2020-11-05
it seems to be working except for the error - "failed to set times on "/var/www/html/" Operation not permitted.
consider it on hold till i do some further research
Thanks

---

### Post by TheFu on 2020-11-05
> **Frank P said:**
> it seems to be working except for the error - "failed to set times on "/var/www/html/" Operation not permitted.
consider it on hold till i do some further research
Thanks

Which file systems are on both sides?  Time issues usually happen when one side isn't using a Unix file system, IME.
/var/www/ is normally owned by www-data:www-data, so if your userid hasn't been added to the www-data group and that group isn't setup with setgid bit and write permissions, then problems will continue. Check the parent directory permissions too.

BTW, with rsync, the trailing '/' on a source directory is important. When I want to mirror A-->B, I use 
```
rsync -avz    A/      B/
```

And if I want more details, I'll use --stats, --progress options.

---

### Post by Frank P on 2020-11-05
192.168.1.89
```

lsblk -no FSTYPE
squashfs
squashfs


ext4

```
192.168.1.87
```

squashfs
squashfs


ext4

LVM2_member
ext4

```
I'll recheck all the owners & permission settings and the trailing slash
Thanks
Frank

---


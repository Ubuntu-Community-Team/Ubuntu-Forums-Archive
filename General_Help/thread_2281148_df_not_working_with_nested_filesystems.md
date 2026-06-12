---
title: "df not working with nested filesystems"
date: 2015-06-04
forum: General Help
---

### Post by George_Dimitoglou on 2015-06-04
Hello, 
On a 14.04.2 LTS I am attempting to do a nested mount from other *nix servers. Example* /etc/fstab*:

```

server01:/vol/data/part01    /data/external/diskA           nfs    ro,soft,intr,nobootwait    0 0 
server01:/vol/data/part02    /data/external/diskB           nfs    ro,soft,intr,nobootwait    0 0
server01:/vol/data/part03    /data/external/diskC           nfs    ro,soft,intr,nobootwait    0 0
server01:/vol/data/part04    /data/external/diskD           nfs    ro,soft,intr,nobootwait    0 0
server**02**:/widgets/part05    /data/external/diskE           nfs    ro,soft,intr,nobootwait    0 0
```

The /data/external/disk* directories have been created.

When I *mount -a* I get no errors and I am able to access every single one of the mounted filesystems without any problems. However, *df* shows only:

```

server01:/vol/data/part02  /data/external/diskB          
server02:/widgets/part05   /data/external/diskE
```

I can *umount -f *each one of them and they also *umount* without a problem. 

I have tried this exercise from the command prompt (not using /etc/fstab) with the same results.

So the NFS mounting works perfectly but *df* is failing. I depend on df on a variety of scripts (backups, checking sizes etc) and I would really like to have it working again. Anyone has seen this before?

Thanks,
George
System: On Ubuntu 14.04.2 LTS
Kernel: 3.16.0-30-generic #40~14.04.1-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux

---

### Post by bab1 on 2015-06-04
> **George_Dimitoglou said:**
> Hello, 
On a 14.04.2 LTS I am attempting to do a nested mount from other *nix servers. Example* /etc/fstab*:

```

server01:/vol/data/part01    /data/external/diskA           nfs    ro,soft,intr,nobootwait    0 0 
server01:/vol/data/part02    /data/external/diskB           nfs    ro,soft,intr,nobootwait    0 0
server01:/vol/data/part03    /data/external/diskC           nfs    ro,soft,intr,nobootwait    0 0
server01:/vol/data/part04    /data/external/diskD           nfs    ro,soft,intr,nobootwait    0 0
server**02**:/widgets/part05    /data/external/diskE           nfs    ro,soft,intr,nobootwait    0 0
```

The /data/external/disk* directories have been created.

When I *mount -a* I get no errors and I am able to access every single one of the mounted filesystems without any problems. However, *df* shows only:

```

server01:/vol/data/part02  /data/external/diskB          
server02:/widgets/part05   /data/external/diskE
```

I can *umount -f *each one of them and they also *umount* without a problem. 

I have tried this exercise from the command prompt (not using /etc/fstab) with the same results.

So the NFS mounting works perfectly but *df* is failing. I depend on df on a variety of scripts (backups, checking sizes etc) and I would really like to have it working again. Anyone has seen this before?

Yes.  It is the [**expected result**]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=737399#20").  It may not necessarily be the result you need.  See if **[FONT=Courier]df -ah[/FONT] **  provides what you want.

---

### Post by George_Dimitoglou on 2015-06-08
Thank you, df -ha does the trick.  

Even though I was perfectly happy with the way it was working without the -a in 10.04 LTS :)

Now I have to go through all my scripts that were depending on checking mount points and filesystems to make sure they don't complain.

---


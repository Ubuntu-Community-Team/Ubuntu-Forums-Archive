---
title: "munge instalation on Ubuntu 20 LTS"
date: 2020-10-13
forum: General Help
---

### Post by marcingronowski on 2020-10-13
Dear Friends,

I have tried to install Munge on two computers (comp1 and comp2) with Ubuntu 20.04.1 LTS. I did many trials, but non of them works. The final one was following:

 On both mashines, I did:
 ```
export MUNGEUSER=64029
 groupadd -g $MUNGEUSER munge
 useradd -m -c "MUNGE Uid 'N' Gid Emporium" -d /var/lib/munge -u $MUNGEUSER -g munge -s /sbin/nologin munge
 apt-get install munge
 apt-get install libmunge-dev
```

 I generated the key on comp1:
 ```
cd /etc/munge/
 create-munge-key
```

 and copied to comp2:
 ```
rsync root@comp1:/etc/munge/munge.key /etc/munge/
```
 
finaly, on botch michenes I did:
 ```
chown -R munge: /etc/munge/
 chown -R munge: /var/log/munge/
 chown -R munge: /var/lib/munge/
 chown -R munge: /run/munge/
 chmod 0700 /etc/munge/
 chmod 0700 /var/log/munge/
 chmod 0700 /var/lib/munge/
 chmod 0700 /run/munge/
 systemctl enable munge
 systemctl start munge
 munge -n | ssh localhost unmunge
```
 The last line worked fine, but non of the folowing:
 ```
root@comp1:/# munge -n | ssh comp2 unmunge
 unmunge: Error: Invalid credential
 
```
 ```
root@comp2:/# munge -n | ssh comp1 unmunge
 unmunge: Error: Invalid credential
 
```

 I checked the UID/GID on botch computers:

 ```
root@comp1:/# cat /etc/group | grep mung
 munge:x:64029:
 root@comp1:/# cat /etc/passwd | grep mung
 munge:x:64029:64029:MUNGE Uid 'N' Gid Emporium:/var/lib/munge:/sbin/nologin
 
```


 ```
root@comp2:/# cat /etc/group | grep mun
 munge:x:64029:
 root@comp2:/# cat /etc/passwd | grep mun
 munge:x:64029:64029:MUNGE Uid 'N' Gid Emporium:/var/lib/munge:/sbin/nologin
 
```
Do you have any suggestions why it doesn't work?

---


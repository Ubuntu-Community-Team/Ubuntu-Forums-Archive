---
title: "network mount folder for none root user"
date: 2013-02-02
forum: General Help
---

### Post by spacecakes on 2013-02-02
Hi, iam trying to mount a dir to my tvheadend user from another box, its mounted with smb but i cant figure out how to give the tvheadend user permissions to record to i? Root user can make folder etc in the dir but cannot chmod it 777 even though it should be mounted as 0777 in fstab.

---

### Post by Morbius1 on 2013-02-02
A simple 2 sentence description of an issue that requires so much information for anyone here to answer.
> iam trying to mount a dir to my tvheadend user from another boxI'm guessing from the subsequent statement that you created a samba share on Box1 for Box2 to access but no one knows how you created it and how it was configured. Posting the output of each of the following commands would help:
```
testparm -s
net usershare info --long
```> its mounted with smb but i cant figure out how to give the tvheadend user permissions to record to i?Gigolo ?
Nautilus ?
fstab?

Where are you mounting it and how?
> Root user can make folder etc in the dir but cannot chmod it 777 even though it should be mounted as 0777 in fstab.  Sounds like it's a NTFS partition since that's one that you cannot chmod and one that can have permissions set in fstab. Post the output of this one:
```
 cat /etc/fstab
```

---

### Post by spacecakes on 2013-02-02
> **Morbius1 said:**
> A simple 2 sentence description of an issue that requires so much information for anyone here to answer.
I'm guessing from the subsequent statement that you created a samba share on Box1 for Box2 to access but no one knows how you created it and how it was configured. Posting the output of each of the following commands would help:
```
testparm -s
net usershare info --long
```Gigolo ?
Nautilus ?
fstab?

Where are you mounting it and how?
Sounds like it's a NTFS partition since that's one that you cannot chmod and one that can have permissions set in fstab. Post the output of this one:
```
 cat /etc/fstab
```

sorry for the confusion, let me clearify: Its mounted with fstab with this line 
//192.168.1.2/share    /home/hts/.hts/tvheadend/serverr        cifs    credentials=/home/patric/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

and its xfs not ntfs

---

### Post by Morbius1 on 2013-02-02
Go to whatever box is 192.168.1.2 and get the other ting that's needed:
```
testparm -s
net usershare info --long
```

---

### Post by spacecakes on 2013-02-02
> **Morbius1 said:**
> Go to whatever box is 192.168.1.2 and get the other ting that's needed:
```
testparm -s
net usershare info --long
```


[root@Server patric]# testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = MSHOME
        idmap config * : backend = tdb

[share]
        path = /home/patric/raid/
        valid users = patric
        read only = No
[root@Server patric]# net usershare info --long
net usershare: usershares are currently disabled

---


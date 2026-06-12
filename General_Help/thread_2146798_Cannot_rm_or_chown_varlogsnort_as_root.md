---
title: "Cannot rm or chown /var/log/snort as root"
date: 2013-05-19
forum: General Help
---

### Post by OtagoHarbour on 2013-05-19
I am using Ubuntu 11.10 Gnome.

I installed an older version of Snort, uninstalled it and tried to  install the latest version as root using sudo.  However, the install  crashed because root does not have permission to change or remove  /var/log/snort.  I thought root was supposed to have permuission to do  anything.  At least it should IMO.

```

ls -ld /var/log/snort 

```

returns

          ```

drwxr-s--- 2 snort adm 4096 2013-05-16 21:17 /var/log/snort 

```

Can anyone suggest a resolution to this problem.

Thanks,
Peter.

---

### Post by redmk2 on 2013-05-19
> **OtagoHarbour said:**
> I am using Ubuntu 11.10 Gnome.

I installed an older version of Snort, uninstalled it and tried to  install the latest version as root using sudo.  However, the install  crashed because root does not have permission to change or remove  /var/log/snort.  I thought root was supposed to have permuission to do  anything.  At least it should IMO

....

Can anyone suggest a resolution to this problem.

Thanks,
Peter.
Root does not have absolute rights. The file (directory) attributes can be set to immutable using ***chattr***.  Those files can't be altered until the immutable bit is turned off.  You can view the attributes with the command ***lsattr***.  The attributes are listed on the ***chattr*** man page```
man chattr
```

The command to list the attributes for the directory would be ```
sudo lsattr -d /var/log.snort 
```...and the command for the files therein would be ```
sudo  lsattr /var/log/snort
```

FYI from the man pages```
A file with the `i' attribute cannot be modified: it cannot be deleted or renamed, no link
       can be created to this file and no data can be written to the file.  Only the superuser or
       a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

```

---

### Post by OtagoHarbour on 2013-05-20
> **redmk2 said:**
> Root does not have absolute rights. The file (directory) attributes can be set to immutable using ***chattr***.  Those files can't be altered until the immutable bit is turned off.  You can view the attributes with the command ***lsattr***.  The attributes are listed on the ***chattr*** man page```
man chattr
```

The command to list the attributes for the directory would be ```
sudo lsattr -d /var/log.snort 
```...and the command for the files therein would be ```
sudo  lsattr /var/log/snort
```

FYI from the man pages```
A file with the `i' attribute cannot be modified: it cannot be deleted or renamed, no link
       can be created to this file and no data can be written to the file.  Only the superuser or
       a process possessing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.

```

Thank you for your reply.

```
sudo lsattr -d /var/log.snort 
```

returned

```
lsattr: No such file or directory while trying to stat /var/log.snort
```

```
sudo  lsattr /var/log/snort
```

returned

```
-----a-----------e- /var/log/snort/alert
-----a-----------e- /var/log/snort/alert.1.gz
-----a-----------e- /var/log/snort/alert.2.gz
-----a-----------e- /var/log/snort/alert.3.gz
-----a-----------e- /var/log/snort/alert.4.gz
-----a-----------e- /var/log/snort/alert.5.gz
-----a-----------e- /var/log/snort/alert.6.gz
-----a-----------e- /var/log/snort/alert.7.gz
-----a-----------e- /var/log/snort/tcpdump.log.1361537869
-----a-----------e- /var/log/snort/tcpdump.log.1361624018
-----a-----------e- /var/log/snort/tcpdump.log.1361709620
-----a-----------e- /var/log/snort/tcpdump.log.1361795972
-----a-----------e- /var/log/snort/tcpdump.log.1361883741
-----a-----------e- /var/log/snort/tcpdump.log.1361969023
-----a-----------e- /var/log/snort/tcpdump.log.1362055135
-----a-----------e- /var/log/snort/tcpdump.log.1362141686
-----a-----------e- /var/log/snort/tcpdump.log.1362160978
-----a-----------e- /var/log/snort/tcpdump.log.1362227876
-----a-----------e- /var/log/snort/tcpdump.log.1362315310
-----a-----------e- /var/log/snort/tcpdump.log.1362401008
-----a-----------e- /var/log/snort/tcpdump.log.1362487641
-----a-----------e- /var/log/snort/tcpdump.log.1362574709
-----a-----------e- /var/log/snort/tcpdump.log.1362660537
-----a-----------e- /var/log/snort/tcpdump.log.1362747549
-----a-----------e- /var/log/snort/tcpdump.log.1362834052
-----a-----------e- /var/log/snort/tcpdump.log.1362916365
-----a-----------e- /var/log/snort/tcpdump.log.1363003251
-----------------e- /var/log/snort/tcpdump.log.1365638373
-----------------e- /var/log/snort/tcpdump.log.1365642298
-----------------e- /var/log/snort/tcpdump.log.1365642397
-----------------e- /var/log/snort/tcpdump.log.1365642556
-----------------e- /var/log/snort/tcpdump.log.1365643063
-----------------e- /var/log/snort/tcpdump.log.1365643615
-----------------e- /var/log/snort/tcpdump.log.1365645774
-----------------e- /var/log/snort/tcpdump.log.1365647668
-----------------e- /var/log/snort/tcpdump.log.1365997593
-----------------e- /var/log/snort/tcpdump.log.1368753466

``` 

Seems the only attribute they all have in common is e.

I tried

```

sudo chattr -e snort

```

and got the error message

```

Clearing extent flag not supported on snort

```

I got the same message when I tried

```

sudo chattr -e snort/*

```

Thanks,
Peter.

---

### Post by OtagoHarbour on 2013-05-20
```
sudo chattr -i snort/*
```

enabled me to remove the contents of /var/log/snort although the i attribute did not appear to have been set.

However ```
sudo chattr -i snort
```

did not allow me to remove /var/log/snort itself.

---

### Post by redmk2 on 2013-05-21
> **OtagoHarbour said:**
> ```
sudo chattr -i snort/*
```

enabled me to remove the contents of /var/log/snort although the i attribute did not appear to have been set.

However ```
sudo chattr -i snort
```

did not allow me to remove /var/log/snort itself.

My mistake.  This: *sudo lsattr -d /var/log.snort* should have been ```
sudo lsattr -d /var/log'snort
```...this should give you the attributes for the directory.

---


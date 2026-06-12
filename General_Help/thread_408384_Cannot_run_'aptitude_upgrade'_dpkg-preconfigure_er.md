---
title: "Cannot run 'aptitude upgrade' dpkg-preconfigure error"
date: 2007-04-13
forum: General Help
---

### Post by xadium on 2007-04-13
When I try to run [FONT="Courier New"]aptitude upgrade[/FONT] I get the following:

```
Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
Reading extended state information                                              
Initializing package states... Done                                             
Building tag database... Done                                                   
The following packages will be upgraded:                                        
  desktop-file-utils libcdparanoia0 linux-image-2.6.17-11-server                
  linux-libc-dev                                                                
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.         
Need to get 0B/25.2MB of archives. After unpacking 12.3kB will be used.         
Do you want to continue? [Y/n/?]                                                
Can't ignore signal CHLD, forcing to default.                                   
Preconfiguring packages ...                                                     
E: Waited for /usr/sbin/dpkg-preconfigure --apt || true but it wasn't there     
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true             
A package failed to install.  Trying to recover:                                        
ali@penfold:~$             
```


I've looked on the forums and there seem to be two suggestions: re-linking /bin/sh to /bin/bash or amending my sources list.  Neither of these seem correct or work.

Anyone got any ideas?  Cheers!

---

### Post by zvacet on 2007-04-13
You are missing dpkg-preconfigure file.Try with 
```
sudo aptitude install dpkg
```

---

### Post by xadium on 2007-04-18
Nooo, it's there...!!



```
ali@penfold:~$ ls /usr/sbin/dpkg-preconfigure -l                                
-rwxr-xr-x 1 root root 3351 Jul 24  2006 /usr/sbin/dpkg-preconfigure            
ali@penfold:~$ file /usr/sbin/dpkg-preconfigure                                 
/usr/sbin/dpkg-preconfigure: awk script text                                    
ali@penfold:~$ stat /usr/sbin/dpkg-preconfigure                                 
  File: `/usr/sbin/dpkg-preconfigure'                                           
  Size: 3351            Blocks: 8          IO Block: 131072 regular file        
Device: 306h/774d       Inode: 760         Links: 1                             
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)        
Access: 2007-04-18 13:33:36.000000000 +0100                                     
Modify: 2006-07-24 16:19:45.000000000 +0100                                     
Change: 2006-11-09 13:02:20.000000000 +0000                                     
ali@penfold:~$           
```

---


---
title: "move /tmp to different existing partition with symlinks?"
date: 2008-01-07
forum: General Help
---

### Post by PetePete on 2008-01-07
I currently have 2 partitions a / and a /home 
/home contains home directories as well as a folder /home/files which is music/media etc...
I want /tmp to actually link to /home/files/tmp

can this be done with a symlink? so when programs access /tmp it is actually accessing /home/files/tmp 

I would use fstab but my understanding is that id have to create a whole new partition (like i did with /home)

---

### Post by PetePete on 2008-01-08
well i tried this, using 
```

mv /tmp /home/files
ln -s /home/files/tmp /tmp 

```
then tried to login (kubuntu so kdm) and kde refused to load :( just crashed everything

im not too hot on symlinks, so maybe this could be done with different syntax?

---

### Post by cherokeejones on 2008-01-08
I don't believe symbolic links can span partitions.

peace,
Cherokee

---

### Post by chrisccoulson on 2008-01-08
If the symlink option doesn't work, you can use a bind mount:
```
sudo mount --bind /home/files/tmp /tmp
```

In your fstab:
```
/home/files/tmp  /tmp  none  defaults,bind  0  0
```

---

### Post by g2g591 on 2008-01-08
actually sym links are able to cross partations, its regular hard links that can't, 
I think [chrisccoulson]("http://ubuntuforums.org/member.php?u=126361")'s solution is the best way to go, but if you want to troubleshoot this solution, this might be a permissions issue, check to make sure that the owner of /home/files/tmp is root and its chmoded to 777. ```
 sudo chown -R root:root /home/files/tmp
sudo chmod -R 777 /home/files/tmp 
```

---

### Post by dagnabit dang doohickey on 2008-01-08
The permissions for tmp should also have the sticky bit set:
```
chmod 1777 /home/files/tmp
```

Also: the use of the recursive option (-R) with chmod and chown on tmp is not necessary and may cause problems until your next reboot.

---


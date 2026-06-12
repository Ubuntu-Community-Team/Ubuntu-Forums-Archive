---
title: "Help with shared folder / acl / permissions"
date: 2016-06-29
forum: General Help
---

### Post by rob-from-canada on 2016-06-29
Hi... been wanting to ask this question for a few days now, but took me a while to figure out how to login here. :D

I  have Ubuntu 16.04, three users: rob, notrob, and guest. I want to share a folder between these two accounts, so that we can add, remove, basically collaborate in the folder. Our home directory looks like this:
```
/home/rob
/home/notrob
/home/sharing
```

```
cd /home
ls -la
drwr-xr-x        2  guest    guest   4096  <date> guest
drwr-xr-x        2  notrob  notrob  4096  <date> notrob
drwr-xr-x        4  rob       rob      4096   <date   rob
drwxrwxr-x+   8  sharing sharing 4096  <date> sharing
```

I followed the directions here [LINK]("https://askubuntu.com/questions/52584/how-do-i-set-up-a-folder-so-that-anything-created-in-it-inherits-permissions")

Unfortunately, only notrob is able to access the folder. rob cannot even list the contents of /sharing

```
notrob@old-laptop:/home$ sudo getfacl sharing/
# file: sharing/
# owner: rob
# group: sharing
user::rwx
group::r-x
group:sharing:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::r-x
default:group:sharing:rwx
default:mask::rwx
default:other::r-x

```
As a bonus, it would be nice if the guest account wasn't able to read or see anything in the directories. 

Thanks,

---

### Post by fdrake on 2016-06-30
```

sudo groupadd sharedGroup
sudo usermod -a -G sharedGroup rob
sudo usermod -a -G sharedGroup notrob
sudo chgrp -R  sharedGroup /home/sharing
sudo chmod 770

``` 

now all the users that will be added to the sharedGroup will be able to Read/Write/Execute content of the folder sharing (including the owner of course).

---


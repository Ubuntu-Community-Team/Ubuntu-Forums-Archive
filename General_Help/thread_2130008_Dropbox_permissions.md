---
title: "Dropbox permissions"
date: 2013-03-28
forum: General Help
---

### Post by spookybathtub on 2013-03-28
I'm using Dropbox to sync files between Ubuntu and Mac OS X.  I want new files in a particular Dropbox folder to inherit 664 permissions to share with another user, but it's not working.
So I have a secondary group, called sharing, with members elliott and rtorrent.  Dropbox is running under elliott, and I want rtorrent to be able to read/write files in a particular Dropbox folder called auto-torrents.
I set the GID:
 ```
chmod g+s /music
```
Then I set ACL's like so:
```
# file: auto-torrents/# owner: elliott
# group: torrents
# flags: -s-
user::rwx
group::r-x
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:mask::rwx
default:other::r-x
```
Permissions look like this:
```
drwxrwsr-x+ 6 elliott torrents   32768 Mar 27 21:39 auto-torrents/
```

When elliott creates files in that folder using *touch*, they are owned by *elliott:**torrents*, and the user rtorrent can delete them.  Great.  But when files are synced by Dropbox, they are owned by *elliott:elliott*&#8203;.  How can I fix this?

---


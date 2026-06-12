---
title: "Cannot access files on external hard drive from non root user on samba"
date: 2019-08-13
forum: General Help
---

### Post by suhassumukh on 2019-08-13
Hello, 
I'm bit of a newbie, in terms of ubuntu and samba. I'm trying to set up a simple samba share. The shared directory is called "/home/su/sharable". The directory contains two files. FileA which is a local resident (i.e. /home/su/sharable/fileA) and FileB which is on an external drive (NTFS). Hence I created a symlink and put in "sharable" directory called "symFileB". For this particular share, the conf has,
```

[sharable]
path=/home/su/sharable
valid users=su, otherguy

```

When I log into my client as user "su" (who is a part of sudoers group), I see both the files. But when I log in as user "otherguy" (not a sudoer), I see only fileA. 
What do I do? How do I make "otherguy" see both the files as well?

---


---
title: "Trouble with subversion"
date: 2006-09-29
forum: General Help
---

### Post by grte on 2006-09-29
Hey, I'm trying to get my hands on a copy of ncmpc-svn, and I'm uspposed to use the command
```
svn co https://svn.musicpd.org/ncmpc/trunk ncmpc
```
but when I do that, I get this error:
```
svn: Can't open config file '/home/avatar/.subversion/servers'
```

Anyone know what the problem is?

---

### Post by JoshHendo on 2006-09-29
Check the permissions for '/home/avatar/.subversion/servers', and also check that it exists. Press Ctrl-H to show hiden files in your home directory.

Also, check it exists. One more thing, is that your user name (avatar) or another users?

- Josh

---

### Post by grte on 2006-09-29
Err, nevermind, I figured it out.  For some reason, .subversion was a file and not a directory.

---


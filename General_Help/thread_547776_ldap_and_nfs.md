---
title: "ldap and nfs"
date: 2007-09-10
forum: General Help
---

### Post by bradleyd on 2007-09-10
hello everyone,

I have setup a ldap server which I can authenticate to. I have autofs mounting the home dir's on the client machine. The only problem is when I try to login or enter the mounted home dir's I get permission denied. I cant seem to find any docs explaining do I need to enter something in ldap or make /home dir's have a certain group or gid? Any help would be great.
Brad

---

### Post by Robstarusa on 2007-10-26
Did you get this figured out?  I'm interesed in any answer you might have been able to obtain.

---

### Post by bradleyd on 2007-10-26
I just made the directories have the same uid and gid as the corresponding login name.

---


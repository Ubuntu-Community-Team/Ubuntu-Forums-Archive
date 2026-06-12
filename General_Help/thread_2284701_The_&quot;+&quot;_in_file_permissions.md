---
title: "The &quot;+&quot; in file permissions"
date: 2015-07-01
forum: General Help
---

### Post by shag00 on 2015-07-01
I can find but already know what the other characters in the permission are however I cannot find any info on the "+". I have the following excerpt from a ls -al enquiry:

 drwxr-x---*+* 21 root root 4096 Jul  1 19:18 

What does the + mean (before the 21)?

---

### Post by Dennis N on 2015-07-01
> **shag00 said:**
> I can find but already know what the other characters in the permission are however I cannot find any info on the "+". I have the following excerpt from a ls -al enquiry:

 drwxr-x---*+* 21 root root 4096 Jul  1 19:18 

What does the + mean (before the 21)?

It means this directory has an access control list.

---

### Post by slickymaster on 2015-07-01
It means that the it has extended permissions called [ACL]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/ch-acls.html")s. You have to run ```
getfacl fileOrDirName
``` to see the full permissions.

---

### Post by Lars Noodén on 2015-07-01
You can read more about ACLs here:

[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)

and in particular the manual pages for [getfacl](http://manpages.ubuntu.com/manpages/trusty/man1/getfacl.1.html) and [setfacl](http://manpages.ubuntu.com/manpages/trusty/man1/setfacl.1.html)

They're useful in some specific cases but not widely used.

---

### Post by Dennis N on 2015-07-01
A bit more:
Can be seen for your /media/<user> directory:

```
dmn@Daphne /media $ ls -al
total 12
drwxr-xr-x   3 root root 4096 Jun 17 10:40 .
drwxr-xr-x  23 root root 4096 Jun 17 10:20 ..
[COLOR="#FF0000"]drwxr-x---+  4 root root 4096 Jul  1 04:21 dmn
[/COLOR]
dmn@Daphne /media $ getfacl dmn
# file: dmn
# owner: root
# group: root
user::rwx
user:dmn:r-x
group::---
mask::r-x
other::---

```
getfacl tells you the permissions and who has them.

How cool is that?

---

### Post by shag00 on 2015-07-01
Thanks guys for a super quick response, now I know what the "+" means I was able to read up further and perform the following commands:
setfacl -b, setfacl -x, setfacl -X and setfacl -k which has reduced the the output of getfacl to:

# file: scott
# owner: root
# group: root
user::rwx
group::---
other::---

I think what I was really after was a command to turn acl off completely for this directory so getfacl would return nil output or error etc. How to achieve this?

---

### Post by shag00 on 2015-07-01
OK SOLVED!!!

command: chacl -B filename

---


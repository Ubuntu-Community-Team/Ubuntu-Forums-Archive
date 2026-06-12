---
title: "group access"
date: 2007-03-09
forum: General Help
---

### Post by mxsteini on 2007-03-09
Hi there,
I don't understand that permission stuff.
I've the following configueration:
User: steini / Group: steini,www-data
and
User: www-data / Group: www-data

And the file:
-rw-rw---- 1 www-data www-data  4220 2007-03-09 15:38 locallang.xml

And the problem:
steini can not access this file - why?
Do I have to reboot after changing group-membership?

Thanks for help

---

### Post by SyvanX on 2007-03-09
Your /etc/group file should have a line like below, the www-data line should be there, you just need to add the user: steini.  I don't think a reboot is necessary.

```
www-data:x:33:**steini**
```

Otherwise, the file pemission looks ok.

---

### Post by ben.s on 2007-03-09
You probably shouldn't muck with /etc/group manually.  There are CLI tools to do what you need.

"groups steini" should return
steini www-data

 --if it doesn't, issue:
"sudo usermod -G www-data steini"

You might need to log out/back in, or start a new shell, but you don't need to reboot.

---


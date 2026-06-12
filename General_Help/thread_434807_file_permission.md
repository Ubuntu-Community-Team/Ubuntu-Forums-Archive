---
title: "file permission"
date: 2007-05-06
forum: General Help
---

### Post by xtremer on 2007-05-06
hey guys 
am new to linux, and i just installed ubuntu 6.10 on a compaq laptop,everything is goin fine, but i need to change the mac address of the netwrok card ,bcoz my internet is workin on the mac add. of the desktop,
so i tried to write this line in "hwaddress ether 01:02:03:04:05:06" in  /etc/network/interfaces
but this file is read only and i cant change it , even am i the root , but the error keeps appearing u r not the owner, so plz guys i need a solution.
10x

---

### Post by taurus on 2007-05-06
You are _not_ root.  You do, however, have a root privilege to edit system files.  Therefore, you need to use the sudo/gksudo command.

```
glsudo gedit /etc/network/interfaces
```

---

### Post by xtremer on 2007-05-06
ur code worked to open the file , i added my code ,but when it comes to save ,this error appears " could not save the file"  "unexpected error: file not found"  :S
wat should i do ?

---

### Post by taurus on 2007-05-06
What's the output of these two commands from a terminal?

```
id
ls -la /etc/network
```

---

### Post by xtremer on 2007-05-06
i tried this command to change the permissions "chmod -r foldername" but alos an error appears: operation not permitted

---


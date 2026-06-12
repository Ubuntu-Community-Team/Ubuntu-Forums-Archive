---
title: "What is this, with files using &quot;ls&quot;"
date: 2007-08-24
forum: General Help
---

### Post by herbster on 2007-08-24
I did:

```
scp file.jpg user@website.com:public_html
```

to upload some pics to show a friend, and I just did one and it was fine, then I upped a few more and I keep getting "403 Permission Denied" when trying to view them.

When I do "ls" in the ssh session, the file.jpg shows up with a * beside it. What does this mean?

TIA! :)

---

### Post by 505 on 2007-08-24
don't know what the * means, but when you do 'ls -l' what are the results? I presume the owner is user, group user... make sure that the files are readable by other. In 'ls -l' check the persmission before each line. The third one from the right should be a 'r'. If not, try 'chmod o+r file.jpg' and see if it works.

---

### Post by herbster on 2007-08-24
That worked great! Pic is visible now just fine in browser, it still has the * beside it though. What does "o+r" command mean exactly? Would like to know for future reference.

---

### Post by 505 on 2007-08-25
chmod allows you to modify file permissions. Each files has three types of permission:
1. for the owner, 2. for the group, 3. for other.
Furthermore, there are three kinds of permission:
1. read, 2. write, 3. execute (run as program, script).

In o+r, the first letter set for whom the permission is changes. 'o' means other. You can also use 'u' (user) or 'g' (group). The '+' means add permission. YOu can also use '-' to take a permission away. 'r' means 'read', this o+r is 'add read permission for others. You can also use 'w' (write) or 'x' (execute).
More information can be found by typing 'man chmod' in a terminal.

---

### Post by herbster on 2007-08-29
> **505 said:**
> chmod allows you to modify file permissions. Each files has three types of permission:
1. for the owner, 2. for the group, 3. for other.
Furthermore, there are three kinds of permission:
1. read, 2. write, 3. execute (run as program, script).

In o+r, the first letter set for whom the permission is changes. 'o' means other. You can also use 'u' (user) or 'g' (group). The '+' means add permission. YOu can also use '-' to take a permission away. 'r' means 'read', this o+r is 'add read permission for others. You can also use 'w' (write) or 'x' (execute).
More information can be found by typing 'man chmod' in a terminal.

505,

Thanks so much! That is a much-needed and thankfully simple explanation, I really needed that!! :)

---

### Post by p_quarles on 2007-08-29
Do you administer this web site yourself? I ask because the "*" tag (along with @ and / ) would show up if the administrator has aliased "ls" to "ls -F". *=executable, @=symlink, /=directory. It's not the default setting on Ubuntu, though.

---


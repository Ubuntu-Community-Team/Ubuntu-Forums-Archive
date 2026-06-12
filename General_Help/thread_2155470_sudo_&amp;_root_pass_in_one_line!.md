---
title: "sudo &amp; root pass in one line!?"
date: 2013-06-18
forum: General Help
---

### Post by shirani on 2013-06-18
Hi;
I need a command in terminal to use sudo and the root password in a single line!
In general we enter sudo and then terminal prompt us to insert pass but i wanna to insert sudo and pass in one step!
Is it possible?:confused:

J.S
Be free...

---

### Post by Lars Noodén on 2013-06-18
You can set specific programs to not need passwords in sudo, but you have to be careful in setting it up.

Here is one example:

```

%adm ALL=(ALL) NOPASSWD: /sbin/ifconfig eth0 *

```

It allows anyone in the group *adm* to adjust the interface eth0.

---

### Post by NikTh on 2013-06-18
For one time you can do 
```
echo "password here" | sudo -S apt-get update && history -c
``` 

The **apt-get update** command is an example here, you can replace it with yours. 

[s]The passwd file contains your password and because of it is dangerous to have your password in a text file, the last command **rm passwd** will remove this text file at the end.[/s]

The **history -c** will remove all the bash shell's history , where your password is exposed. 

Regards
 NikTh

---

### Post by shirani on 2013-06-18
thx NikTh for your help...

have good times

---

### Post by Lars Noodén on 2013-06-18
That could be boiled down even shorter, skipping the redirect to a file and just piping the echo into sudo.  However, either way you end up with the password unencryped in the shell's history which is a very big risk.  If you do either way, the history should be cleared immediately, *history -c* but if you are using another shell than bash, the method might be different.  I'd advise against anything that puts the password in cleartext.

---

### Post by NikTh on 2013-06-18
> **Lars Noodén said:**
> with the password unencryped in the shell's history....

This is absolutely right !!! I edited my command. !! 

Thanks

---

### Post by shirani on 2013-06-18
Thanks Lars and NikTh...

Have good times....

---

### Post by NikTh on 2013-06-19
Please mark the thread as solved. See my signature for a How To. 

Regards
 NikTh

---


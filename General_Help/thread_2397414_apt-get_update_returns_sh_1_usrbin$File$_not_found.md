---
title: "apt-get update returns sh: 1: /usr/bin/$File$: not found"
date: 2018-07-29
forum: General Help
---

### Post by adam17 on 2018-07-29
Hi all, 

Not sure what I have done or how, was playing around with something a few weeks back and now when i use the command 

```
sudo apt-get update
```

I get the following:

```


Hit:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu bionic InRelease
Hit:3 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:4 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease
sh: 1: /usr/bin/test: not found                    
sh: 1: /usr/bin/test: not found
sh: 1: /usr/bin/test: not found
Reading package lists... Done


```

I dont understand why I am getting the "sh: 1: /usr/bin/test: not found" is it a case of removing a reference to it? I am still learning with Ubuntu.

Anyone able to help, I would appreciate it.

Thanks Adam>

---

### Post by kc1di on 2018-07-29
Looks like your apt source list got corrupted some how and you have an entry pointing toward a local file /usr/bin/test  that is not a good entry.
perhaps you were trying to use a local repository. In any event you'll need to clear that entry in the list.  Can you post the /etc/apt/list and /etc/apt/list.d here.
you can also go to software & updates and find the error lines and delete them. 
good luck.

---

### Post by westie457 on 2018-07-29
Hi, when you were playing around you possibly somehow removed something important (/usr/bin/test) and probably some other files however we don't know what they maybe.
Checking here [https://packages.ubuntu.com/search?searchon=contents&keywords=test&mode=exactfilename&suite=bionic&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=test&mode=exactfilename&suite=bionic&arch=any) we find a missing file.

Try a quick fix ```
sudo apt install --reinstall coreutils
``` followed by ```
sudo apt update
sudo apt upgrade
```
Post back if successful or post any errors if unsuccessful.

---

### Post by adam17 on 2018-07-29
Hi, 

I thanks for the help, I used the ```
sudo apt install --reinstall coreutils
``` and that seems to have worked.

Im not getting an error after ```
sudo apt install update / upgrade
``` now.

Thanks for the help!!

Adam.

---

### Post by westie457 on 2018-07-29
Glad it worked for you otherwise we would have needed to continue with kc1di info finding.
Could you mark as 'solved' please.

---

### Post by #&amp;thj^% on 2018-07-29
> **westie457 said:**
> 
Could you mark as 'solved' please.
I believe OP did this already>>[SOLVED] apt-get update returns sh: 1: /usr/bin/$File$: not found
I'll buy you a cup coffee or tea. ;)

---

### Post by kc1di on 2018-07-29
Glad you got it sorted out :)

---


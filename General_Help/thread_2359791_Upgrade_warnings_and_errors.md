---
title: "Upgrade warnings and errors"
date: 2017-04-27
forum: General Help
---

### Post by sifumaster on 2017-04-27
When i try to upgrade i get all these similar warnings and the errors at the end.Is there anything i can do about it?

[http://paste.ubuntu.com/24469634/](http://paste.ubuntu.com/24469634/)

---

### Post by gsahli on 2017-04-27
Try using another mirror site.

---

### Post by sifumaster on 2017-04-28
How exactly do i do this?

---

### Post by gsahli on 2017-04-28
(This is in 16.04.2)
Go to System > Administration > Software & Updates. In the Ubuntu Software tab (leftmost), find "Download from:" and select one that is close to you.
If that doesn't help, try this command in Terminal:
sudo dpkg --configure -a  (this one is supposed to repair the dpkg/apt database)

---

### Post by sifumaster on 2017-04-29
Tried both of them but neither fixed the problem

---

### Post by mörgæs on 2017-04-30
The only solution I know is to reinstall all the packages mentioned. Luckily it can be done in a loop.

This command may or may not work. I have not tried it myself.

```
for package in $(apt-get upgrade 2>&1 | grep "warning: files list file for package '" | grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do apt-get install --reinstall "$package"; done

```
Found here: 
[https://coderwall.com/p/j-nsmg/fixing-dpkg-warning-files-list-file-for-package-x-missing](https://coderwall.com/p/j-nsmg/fixing-dpkg-warning-files-list-file-for-package-x-missing)

It will probably take long time to execute.

---

### Post by sifumaster on 2017-04-30
I figured out i got no folder named dpkg. I must have deleted it. Dont know if this helps. I tried to do this [https://askubuntu.com/questions/383339/how-to-recover-deleted-dpkg-directory](https://askubuntu.com/questions/383339/how-to-recover-deleted-dpkg-directory) , but it doesnt work for me, because i get the following output 

```
$ apt-get download dpkg
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dpkg amd64 1.18.4ubuntu1.2
  Could not open file /usr/bin/dpkg_1.18.4ubuntu1.2_amd64.deb - open (13: Permission denied) [IP: 91.189.88.152 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.18.4ubuntu1.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.18.4ubuntu1.2_amd64.deb)  Could not open file /usr/bin/dpkg_1.18.4ubuntu1.2_amd64.deb - open (13: Permission denied) [IP: 91.189.88.152 80]
```

---

### Post by mörgæs on 2017-05-01
I wonder why you end up in these situations. A long list of broken packages and now the (directory? / executable?) dpkg is maybe / maybe not missing.

What happens when you run the command mentioned in post 4? Please post the output.

---


---
title: "problem with lamp server"
date: 2008-01-09
forum: General Help
---

### Post by felixdecat on 2008-01-09
I just installed 7.10 ubuntu server l.a.m.p, I keep getting this problem 

I was trying to install webmin but I was gettin this error

```
root@linuxserver:/opt/webmin# sudo apt-get install libauthen-pam-perl libnet-ssleay-perl libpam-runtime openssl perl perl-modules
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libauthen-pam-perl

```

So I thought i just had to update my repository but I got this error

```
bash: /etc/apt/sources.list: Permission denied

```

any help with this would be greatly appreciated

cheers

---

### Post by aJayRoo on 2008-01-09
What command had you typed when you got the permission denied error? If you want to edit the sources list you would need to issue the command:
```
sudo nano /etc/apt/sources.list
```
where nano is a text editor, you could use any editor you like. The libauthen-pam-perl package is in the universe repository so you would then need to make sure that is not commented out in the sources list. Hope that helps.

---

### Post by felixdecat on 2008-01-09
yea Ii figured out how to edit my repository list with nano editor but im still getting the same thing where it cant find any packages.

I just changed the list and un commented all the source lists.

Im getting the same problem when I try```
sudo apt-get install ubuntu-desktop
```

---

### Post by aJayRoo on 2008-01-09
So it is telling you that it cannot find the package, whatever you try to install? Did you run:
```
sudo apt-get update
``` after you updated the sources list? If you still have problems perhaps you could post your sources list and the exact error you are getting along with the command you use when you encounter it. That way some one will probably be able to help you out.

---


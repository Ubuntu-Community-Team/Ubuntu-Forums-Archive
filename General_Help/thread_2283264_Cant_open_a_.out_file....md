---
title: "Cant open a .out file..."
date: 2015-06-20
forum: General Help
---

### Post by tupac2 on 2015-06-20
Hello, 

I have a file "Host.out" it work very well on Centos, sometimes i have to install this to centos to start the file > yum install glibc.i686

But on ubuntu it wont work at all.

When i try to launch the file there is this > [http://puu.sh/ivMvP/85cb698324.png](http://puu.sh/ivMvP/85cb698324.png)

Tried chmod, apt-get install gcc.... still same.

Someone can help me please ?

---

### Post by steeldriver on 2015-06-20
Hello and welcome to the forums

What is Host.out and where did you get it? if it is a compiled binary file that relies on shared libraries, there is no guarantee that it will be able to work on a different system. To start, you could run the following diagnostic commands

```

file Host.out

ldd Host.out

```

Please post the outputs** in text** using the forum's [code] tags

---

### Post by tupac2 on 2015-06-20
Here is :

> 

root@vmi43386:/etc# cd
root@vmi43386:/# cd .script/
[email]root@vmi43386:/.script[/email]# ls
azkdrop  Host.out
[email]root@vmi43386:/.script[/email]# ./Host.out
-bash: ./Host.out: No such file or directory
[email]root@vmi43386:/.script[/email]# cd
root@vmi43386:/# cd
root@vmi43386:/# cd
root@vmi43386:/# cd
root@vmi43386:/# ls
bin   etc         lib         media  proc  sbin  tmp  vmi43386
boot  home        lib64       mnt    root  srv   usr  vmlinuz
dev   initrd.img  lost+found  opt    run   sys   var
root@vmi43386:/# cd .script/
[email]root@vmi43386:/.script[/email]# ls
azkdrop  Host.out
[email]root@vmi43386:/.script[/email]# ./Host.out
-bash: ./Host.out: No such file or directory
[email]root@vmi43386:/.script[/email]# file Host.out
Host.out: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), BuildID[sha1]=24bda89f9361c6ea8bcd356c178a50ec8525dc86, stripped
[email]root@vmi43386:/.script[/email]# ldd Host.out
        not a dynamic executable
[email]root@vmi43386:/.script[/email]# ./Host.out
-bash: ./Host.out: No such file or directory
[email]root@vmi43386:/.script[/email]# mv Host.out /root
[email]root@vmi43386:/.script[/email]# cd /root
root@vmi43386:/root# ls
Host.out
root@vmi43386:/root# ./Host.out
-bash: ./Host.out: No such file or directory
root@vmi43386:/root# ldd Host.out
        not a dynamic executable
root@vmi43386:/root# file Host.out
Host.out: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), BuildID[sha1]=24bda89f9361c6ea8bcd356c178a50ec8525dc86, stripped
root@vmi43386:/root# chmod 777 Host.out
root@vmi43386:/root# ./Host.out
-bash: ./Host.out: No such file or directory




.script/ is a hidden file, i tought it was the problem so i tried to move in root to see if it works,its still same...

Also it work very well on my centos dedicated server, but on ubuntu its looks like it is not considered as an executable:

> 
[email]root@vmi43386:/.script[/email]# ldd Host.out
not a dynamic executable


Also, i can lend the ubuntu dedicated server with ssh privately by message if you want to see and help me, would appreciate a lot.

Best regards and thanking you in advance.

---

### Post by tupac2 on 2015-06-21
anyone to help me ?

---

### Post by steeldriver on 2015-06-21
It looks like you're trying to run a 32-bit executable on a 64-bit system, without the necessary 32-bit support

---

### Post by tupac2 on 2015-06-22
Finally i found the problem, i had to install x32 libraries.

> 
apt-get install lib32ncurses5 lib32bz2-1.0 lib32z1


Problem solved, thank you very much for your help.

---


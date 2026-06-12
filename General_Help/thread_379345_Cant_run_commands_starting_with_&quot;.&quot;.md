---
title: "Cant run commands starting with &quot;./&quot;"
date: 2007-03-08
forum: General Help
---

### Post by Zach1188 on 2007-03-08
For some reason, I cannot run any commands that start with "./", I just get permission denied. The reason I need this is because I am trying to install Linux on my iPod, using this guide: 

[http://www.ipodlinux.org/5.5G#Locating_Your_iPod](http://www.ipodlinux.org/5.5G#Locating_Your_iPod)

When I get to the part where I enter "./ipodpatcher --scan" this is what happens (I tried running as root):

> 
zach@zCOMP:~$ cd Desktop/iLinux
zach@zCOMP:~/Desktop/iLinux$ ./ipodpatcher --scan
bash: ./ipodpatcher: Permission denied
zach@zCOMP:~/Desktop/iLinux$ sudo ./ipodpatcher --scan
Password:
sudo: ./ipodpatcher: command not found
zach@zCOMP:~/Desktop/iLinux$ su
Password: 
root@zCOMP:/home/zach/Desktop/iLinux# ./ipodpatcher --scan
bash: ./ipodpatcher: Permission denied

*Notice, even running as root using su, it still doesn't work. I tried logging in as root entirely (I know it's a bad idea), the exact same thing happened.*


And, it's not just this file. I tried making a .sh file with one command "echo Success," and it doesn't work either:

> 
root@zCOMP:/home/zach/Desktop/iLinux# sh test.sh
Success
root@zCOMP:/home/zach/Desktop/iLinux# ./test.sh
bash: ./test.sh: Permission denied


---

### Post by Ek0nomik on 2007-03-08
Add "sudo" to the front of your command.  It will give you super user privledges.

---

### Post by Zach1188 on 2007-03-08
> 
zach@zCOMP:~$ cd Desktop/iLinux
zach@zCOMP:~/Desktop/iLinux$ ./ipodpatcher --scan
bash: ./ipodpatcher: Permission denied
zach@zCOMP:~/Desktop/iLinux$ sudo ./ipodpatcher --scan
Password:
sudo: ./ipodpatcher: command not found
zach@zCOMP:~/Desktop/iLinux$ su
Password: 
root@zCOMP:/home/zach/Desktop/iLinux# ./ipodpatcher --scan
bash: ./ipodpatcher: Permission denied

*Notice, even running as root using su, it still doesn't work. I tried logging in as root entirely (I know it's a bad idea), the exact same thing happened.*

---

### Post by hinzel on 2007-03-08
strange, what are the file permissions?


does "sudo bash ipodpatcher" give the same error?

---

### Post by Zach1188 on 2007-03-08
Two attempts, neither worked:

> 
root@zCOMP:/home/zach/Desktop/iLinux# sudo bash ./ipodpatcher --scan
./ipodpatcher: ./ipodpatcher: cannot execute binary file
root@zCOMP:/home/zach/Desktop/iLinux# sudo bash ipodpatcher
ipodpatcher: ipodpatcher: cannot execute binary file


---

### Post by dannyboy79 on 2007-03-08
i am guesssing that the file isn't executable? do a ls -la on the directory the file is located in and show us the results. also, do you have python installed?


OK, you should maybe read the guide again, it clearly states, "Linux users may have to use chmod (man chmod) first if they get a 'Permission denied'" I am guessing my first statement is true.

do a sudo chmod uga+x ipodpatcher

and you should be good to go.

---

### Post by Zach1188 on 2007-03-08
> 
total 3424
drwxr-xr-x 2 zach zach    4096 2007-03-08 09:44 .
drwxr-xr-x 3 zach zach    4096 2007-03-08 09:28 ..
-rw-r--r-- 1 zach zach 1048561 2007-03-08 09:19 ipod_fs_220606.tar.gz
-rw-r--r-- 1 zach zach   33167 2007-03-08 09:18 Ipodloader2-2.5d6.tar.gz
-rw-r--r-- 1 zach zach  362352 2007-03-08 09:25 ipodpatcher
-rw-r--r-- 1 zach zach  359424 2007-03-08 09:38 ipodpatcher.exe
-rw-r--r-- 1 zach zach 1659068 2007-03-08 09:19 kernel-dg-all-iPods-improved-20070305.bin
-rw------- 1 zach zach      13 2007-03-08 09:43 test.sh
-rw------- 1 zach zach       0 2007-03-08 09:42 test.sh~
-rw------- 1 zach zach      48 2007-03-08 09:44 Website
-rw------- 1 zach zach       0 2007-03-08 09:44 Website~

Ignore ipodpatcher.exe, earlier I was desperate enough to try running the .exe in crossover.

I don't know if I have python installed.


Edit:
Sorry, I DID read the guide, but I had no idea how to use chmod. It works now, thank you :D

---

### Post by dannyboy79 on 2007-03-08
> **Zach1188 said:**
> Ignore ipodpatcher.exe, earlier I was desperate enough to try running the .exe in crossover.

I don't know if I have python installed.


Edit:
Sorry, I DID read the guide, but I had no idea how to use chmod. It works now, thank you :D


ok, if you don't know how to use chmod, then you need to learn about it. the man pages are a great resource for me. go to a terminal and type in man chmod and it will bring up a "manual" of the chmod command, it's a bit of a technical read but if you want to use linux, then you need to learn about it. good luck with your linux experience. you should really start out reading some linux basics regarding file permission, file attributes, etc etc. it will help you pick up linux a lot faster and also, when you come here for help and people use terms, you'll know what they are talking about.

---

### Post by g3k0 on 2007-03-08
```

-rw-r--r-- 1 zach zach 362352 2007-03-08 09:25 ipodpatcher

```

Glad u got it working. If you don't understand what the letters stand for (which you might understand and this post is pointless) then I'll talk a little

-rwx

Read, Write, eXecute.  There are three setions of these.  The first for the owner, the second for the group, and the third for everyone else.

The first dash can be d for directory or something.  Also if the owners X is S it means it can be run by lower users and the program has access with root permission.. eh thats not explained so well. .. Well dont worry about S.

so if everything is enabled it might be -rwxrwxrwx.  Freedom for all!

---


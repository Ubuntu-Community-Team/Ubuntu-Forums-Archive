---
title: "apt-get vs apt-file"
date: 2006-11-03
forum: General Help
---

### Post by cabotp on 2006-11-03
It would seem that I have a discrepancy between apt-file and apt-get

I'm trying to install the iozone program. So I did the following

1)sudo apt-file search iozone

It told me that the iozone3 package is what I want

So then I did a:

2)sudo apt-get install iozone3

And its giving me a error that the package does not exist

I've already tried doing the following 

sudo apt-get update
sudo apt-file update

But neither solved my problem.

It would seem that apt-file is seeing a package that apt-get can not see.  Anyway to get around this problem? :confused:

---

### Post by loell on 2006-11-03
sudo: apt-file: command not found :-k

---

### Post by ~LoKe on 2006-11-03
> $ sudo apt-get install iozone3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  iozone3
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 384kB of archives.
After unpacking, 643kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse iozone3 257-1 [384kB]
72% [1 iozone3 277698/384kB 72%]
Uncomment the multiverse repository in /etc/apt/sources.list

---

### Post by cabotp on 2006-11-04
> sudo: apt-file: command not found 

Install the apt-file package


> **~LoKe said:**
> Uncomment the multiverse repository in /etc/apt/sources.list

I went into sources.list and uncommented the following line

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

Then I did a "sudo apt-get update"

And then "sudo apt-get install iozone3" and got this output

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package iozone3

---

### Post by loell on 2006-11-04
loell@loell-desktop:~$ apt-cache search iozone3
iozone3 - Filesystem and Disk Benchmarking Tool
loell@loell-desktop:~$ 

why are you using apt-file anyway? do you see any advantage of this tool over apt-get, apt-cache and aptitude?

---

### Post by jocko on 2006-11-04
>  deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper**-backports** main restricted universe multiverse

Maybe it isn't in the backports repo? Try adding this:
```
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper multiverse
```

---

### Post by cabotp on 2006-11-04
> **loell said:**
> loell@loell-desktop:~$ apt-cache search iozone3
iozone3 - Filesystem and Disk Benchmarking Tool
loell@loell-desktop:~$ 

why are you using apt-file anyway? do you see any advantage of this tool over apt-get, apt-cache and aptitude?

With yum if you know the name of a file or part of a name but don't know the package that has that file you can do a simple "yum search *filename*"  And it will give you a list of packages that have that file. 

Now unless there is another of doing the same thing with apt. From what I can read from the docs "apt-file search *filename*"gives me the same function. 

Sorry about the confusion.  I'm just so used to the redhat system and have never used apt 8) 



> **jocko said:**
> Maybe it isn't in the backports repo? Try adding this:
```
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper multiverse
```

Thanks that was it :D

---

### Post by angkor on 2006-11-04
> **loell said:**
> why are you using apt-file anyway? do you see any advantage of this tool over apt-get, apt-cache and aptitude?

'apt-cache search' searches for packages names.
'apt-file search' searches for files within the packages, this can be very helpful when compiling programs.

---

### Post by cabotp on 2006-11-04
Ya especially when your missing that one library file :)

---


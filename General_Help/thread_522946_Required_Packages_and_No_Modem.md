---
title: "Required Packages and No Modem"
date: 2007-08-11
forum: General Help
---

### Post by Desigen on 2007-08-11
Hi, How are you doing?? 

I'm new in Ubuntu and I have two questions. I Google a lot in the last two weeks but I didn't find something that very helpful. 

After installing Ubuntu it didn't install drivers for my modem. And when I download the driver from the Internet and I work throw the Ubuntu's Guide for my Modem, he asks me about Kernel Headers, and some compilers, My questions, how can I get those and I don't have an Internet connection? 

Is there any way to make Ubuntu generate a list of required packages and I use Windows to download those missing packages? 

Also, how can I apply those packages on my PC automatically? 

Thanks 
Bye

---

### Post by zvacet on 2007-08-11
[http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet]("http://ubuntuforums.org/showthread.php?t=475312&highlight=package+no+internet")

---

### Post by Desigen on 2007-08-11
Yeb, that was very helpful. 

I have another question. I did yesterday : apt-get update. I'm planning to install Ubuntu again on another machine. How can I backup the updated packages list and install it on that machine? 

Thanks in advance.

---

### Post by zvacet on 2007-08-11
[http://aptoncd.sourceforge.net/download.html]("http://aptoncd.sourceforge.net/download.html")

---

### Post by Desigen on 2007-08-12
Yes, this is when I want to make a backup copy of my downloaded packages. But what about the list of packages. When I did : apt-get update command Ubuntu update some file "Package Reposotry" How can I copy that file. So I can transfare it to another machine. 

I hope you get what I mean. 

Thanks

---

### Post by capink on 2007-08-12
when you type the command apt-get update a lot of files are updated. They all reside in /var/lib/apt/lists.

if you want the url of packages you can type:

```
sudo apt-get install --print-uris packagename
```

---

### Post by Desigen on 2007-08-12
Thanks, so all I have to do is : tar cvf aptPackageLists /var/lib/apt/lists/* 

And on place those files on the second machine using x option ?? 

Thanks

---

### Post by capink on 2007-08-12
Yes, to backup:

```
sudo tar cvz /var/lib/apt/lists/* -f ~/backup.tgz
```

to restore:

```
sudo tar -xv -f ~/backup.tgz -C /
```

---

### Post by Desigen on 2007-08-12
Thanks a lot. 
Have fun.

---


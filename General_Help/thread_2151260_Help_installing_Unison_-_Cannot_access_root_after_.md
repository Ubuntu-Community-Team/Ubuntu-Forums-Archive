---
title: "Help installing Unison - Cannot access root after changing sources.list"
date: 2013-06-03
forum: General Help
---

### Post by UncleAsriel on 2013-06-03
I'm  attempting to install unison via[ this method]("http://blog.philippheckel.com/2008/05/16/unison-2-27-57-on-debian-etch-and-ubuntu-hardy/"). (Foolish to use something so old, I know, but I was experimenting). I figured I might as well use the command line to get into good habits.




I entered the following
```

$ sudo editor /etc/apt/sources.list

```




I then added the following lines after the three pre-existing commands 


```
deb http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
```


I then to do ```
sudo apt-get update
```, only to recieve the following message:


```
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```


I undid the changes I made (erasing the changes I made to the sources.list), only to fins I still got the same error. 


I read rebooting would fix this. it did not. What should my next move be?

---

### Post by plucky on 2013-06-04
> E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)

Try removing the 'lock' file. ```
sudo rm /var/lib/apt/lists/lock
```

Then running "sudo apt-get update" and see if you still get the error.


> deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

Hardy repositories are closed,so no point in trying to access them.

Good Luck

---

### Post by UncleAsriel on 2013-06-04
A restart this morning somehow saw my ability to use apt-get return.  Odd, but welcome.


It seems that dinkering with the command line to get a PPA from a remote PPA library is less than optimal.

I currently have the extracted .tar.gz file in /Home/, but on entering the directory via cd /unison-2.40.63/, I can't activate the Install files via "sudo ./INSTALL" or "sudo ./INSTALL.gtk2". (There are a few more packages namwed INSTALL, but those are for Windows.)

Can anyone advise?

---


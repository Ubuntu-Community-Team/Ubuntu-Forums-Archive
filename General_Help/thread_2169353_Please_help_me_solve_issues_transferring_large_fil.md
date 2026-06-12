---
title: "Please help me solve issues transferring large files over SSH/SFTP"
date: 2013-08-21
forum: General Help
---

### Post by maxplanck on 2013-08-21
I am running Ubuntu Desktop 13.04 inside a VM.

Currently, I use my remote server to download large files, which I subsequently transfer to my home workstation over SSH/SFTP using Filezilla.  These files tend to be in the 40-50GB range.  To solve the limited speed per *connection*, I simply split large files into chunks of 50MB, then make FileZilla create 10 separate connections to max out my available bandwidth.  

Needless to say, this is a horrifically tedious process - I use x2go to establish a gnome session and use peazip to split things up using the gui.  As embarrassing as this is, I couldn't figure out how to get 7zip to use no (store) compression from the terminal and split up the files.  If I knew how, I could just SSH in and split things up with a simple command.  There must be a better way though, right?

Can anyone suggest a better way to do this or guide me to the right syntax to use a standard archiving tool to split a file , with no compression options, which allows you to specify the split size?

---

### Post by Cheesemill on 2013-08-21
How about the 'split' command ;)

This will split a file into 50MB chunks...
```
split -b 50M filename
```

You can then use cat to join them back together...
```
cat xaa xab xac ... > filename
```

An example...
```
rob@arch:~/ISOs/linux/ubuntu/precise$ ls
total 656M
-rw------- 1 rob users 656M Feb 13  2013 ubuntu-12.04.2-server-amd64.iso
rob@arch:~/ISOs/linux/ubuntu/precise$ split -b 50M ubuntu-12.04.2-server-amd64.iso 
rob@arch:~/ISOs/linux/ubuntu/precise$ ls
total 1018M
-rw------- 1 rob users 656M Feb 13  2013 ubuntu-12.04.2-server-amd64.iso
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaa
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xab
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xac
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xad
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xae
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaf
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xag
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xah
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xai
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaj
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xak
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xal
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xam
-rw-r--r-- 1 rob users 6.0M Aug 21 22:38 xan
rob@arch:~/ISOs/linux/ubuntu/precise$ 
rob@arch:~/ISOs/linux/ubuntu/precise$ 
rob@arch:~/ISOs/linux/ubuntu/precise$ cat xa[a-n] > ubuntu.iso
rob@arch:~/ISOs/linux/ubuntu/precise$ ls
total 1.4G
-rw------- 1 rob users 656M Feb 13  2013 ubuntu-12.04.2-server-amd64.iso
-rw-r--r-- 1 rob users 656M Aug 21 22:40 ubuntu.iso
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaa
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xab
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xac
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xad
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xae
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaf
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xag
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xah
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xai
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xaj
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xak
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xal
-rw-r--r-- 1 rob users  50M Aug 21 22:38 xam
-rw-r--r-- 1 rob users 6.0M Aug 21 22:38 xan
rob@arch:~/ISOs/linux/ubuntu/precise$ 

```

---

### Post by maxplanck on 2013-08-21
Oooo I like when I overlook the obvious.  One problem though, files are going to be transferred to a Windows box.  How can I join them in Windows (will 7zip handle these?)

---

### Post by papibe on 2013-08-21
Hi maxplanck.

I'd use rsync on a script instead. Take a look at post #2 in this [thread]("http://ubuntuforums.org/showthread.php?t=1861143&highlight=rsync+script"), and let us know if that helps, and/or you have more questions.

Regards.

---


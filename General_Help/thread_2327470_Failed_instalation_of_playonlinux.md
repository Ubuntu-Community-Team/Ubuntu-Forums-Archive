---
title: "Failed instalation of playonlinux"
date: 2016-06-11
forum: General Help
---

### Post by Allisterguy on 2016-06-11
Hi 
I have tried twice to install playonlinux  following two U tube videos all seemed to go well but I now get on terminal this error :-"  Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? "

Not sure how to proceed
I am using Ubuntu 16.04
thanks
ACG

---

### Post by howefield on 2016-06-11
Sounds like you already have a package manager running, software updater, synaptic, software centre ect, ect ? If so, close it/them.

---

### Post by Allisterguy on 2016-06-11
Thanks for the reply
I got an agreement type screen like click here to agree to conditions but it would not let me do this  so perhaps this is still running
how do I clear/stop the package manager
thanks for your time.
ACG

---

### Post by howefield on 2016-06-11
> **Allisterguy said:**
> I got an agreement type screen like click here to agree to conditions but it would not let me do this  so perhaps this is still running

Is that the license agreement for the ttf-mscorefonts-installer package that has come up in the terminal ?

If so, use the tab keys to highlight the appropriate reposnse and the enter key to execute it.

---

### Post by Allisterguy on 2016-06-11
Thanks
I cannot get back to that screen.
I had closed down my computer and when I try to access anything on terminal it says ```
dpkg: error: dpkg status database is locked by another process
```
 Dont know how to clear/ and start again
ACG

---

### Post by vasa1 on 2016-06-11
Please post the output of ```
sudo lsof /var/lib/dpkg/lock
```

This is what I see if the Synaptic Package Manager is open when I run the command:```
03:51 PM ~ $ sudo lsof /var/lib/dpkg/lock
[sudo] password for vasa1: 
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
synaptic 4235 root   11uW  REG    8,6        0 12583256 /var/lib/dpkg/lock
03:51 PM ~ $ 
```The line starting with "synaptic" tells me that that is the process the dpkg error refers to.

If you can't close the program by normal gui means, use ```
sudo pkill command-name
``` which is **synaptic** in this example or ```
sudo kill PID
```which is **4235** in this example.

---

### Post by Allisterguy on 2016-06-11
Thanks for your reply
This is all I get:-
```
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
allister@allister-imedia-S2185:~$ 
```
which seems to some thing missing when compared to your output
ACG

---

### Post by howefield on 2016-06-11
Try

```
ps aux | grep apt
```

if you get an apt-get process or an aptitude process in the output, try..

```
kill processnumber
```

---

### Post by Allisterguy on 2016-06-11
This is the reply I get to 
ps aux | grep apt 

allister  2539  0.0  0.0   5112   808 pts/2    S+   14:33   0:00 grep --color=auto apt

not sure what to type in 
ACG

---

### Post by howefield on 2016-06-11
OK, try
	
```
sudo rm /var/lib/dpkg/lock
```
```
sudo dpkg --configure -a
```

---


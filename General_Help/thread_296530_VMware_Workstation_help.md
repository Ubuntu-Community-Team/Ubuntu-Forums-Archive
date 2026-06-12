---
title: "VMware Workstation help"
date: 2006-11-09
forum: General Help
---

### Post by ZERO_SHIFT on 2006-11-09
As I try to install VMware Workstation I get the following:

```
zaid@Johnny:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.


```

What can I do to remove any previous installations?

```
zaid@Johnny:~$ vmware
bash: vmware: command not found

```

---

### Post by Kirky_D on 2006-11-15
I also get this problem, I did try installing it before but it failed for some reason, cant remember now. 

So i get another version and it gives me the same error as yours.

Is there any way to purge the files from the system?

EDIT::

look here

[http://www.vmware.com/community/thread.jspa?messageID=510503](http://www.vmware.com/community/thread.jspa?messageID=510503)

Sorted it for me

---

### Post by jimbob on 2006-11-15
I had this problem too for a while but can't remember exactly what I did to get rid of it.

First, run dpkg -r --purge vmware-player

Then:   cd /
        find . -name "*vmware*"

and remove any and all packages that you find in the list.

I think that cleared it up for me.

EDIT: Now I remember that it was the file in /etc that caused the problem.  /etc/.vmware I think.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---


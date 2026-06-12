---
title: "Problem installing VMWare Server Console"
date: 2008-01-07
forum: General Help
---

### Post by thomasr on 2008-01-07
I am trying to install the VMWare Server Console only - not the whole server package.

When I try to install from source, I get the following error:

The path "/usr/lib/vmware-server-console" does not exist currently. This
program is going to create it, including needed parent directories. Is this
what you want? [yes]

Unable to get the access rights of source file "./lib".

Execution aborted.


Using Kpackage and Alien, I get the following error:
rpm -U --replacepkgs --test '///home/thomas/Desktop/VMware-server-console-1.0.4-56528.i386.rpm';echo RESULT=$?
error: Failed dependencies:
/bin/sh is needed by VMware-server-console-1.0.4-56528.i386
RESULT=1

Any help would be appreciated greatly. I would like to have ther server console only installed so that I can also install VMWare workstation. I was able to do this on earlier versions of Ububntu and mint.

Thanks

---

### Post by paulororke on 2008-01-10
Did you run the pearl installer?  I'm confused as to why you are dealing with the rpm on Ubuntu.

It worked 'right out of the box' for me on Ubuntu 7.10 "gutsy":

[http://docs.paulororke.net/ubuntu/installVMwareServer.php]("http://docs.paulororke.net/ubuntu/installVMwareServer.php")

I'm assuming you ran the script as root.  It will prompt you to do so if you didn't:
```
$ sudo ./vmware-install.pl
```

---

### Post by thomasr on 2008-01-12
I had tried to install from rpm after installing from source failed.

I did a clean install and found that running $ sudo /vmware-install.pl failed, but running
$ sudo ./vmware-install.pl worked. The dot made a difference. Thanks. I am now in virtualization hog heaven - vmware workstation, server console and virtuua box.

Thanks again

---

### Post by paulororke on 2008-01-12
glad to hear it worked out.  The . or more specifically ./ represents the current directory you are in.

---


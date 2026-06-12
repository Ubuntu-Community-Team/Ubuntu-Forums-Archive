---
title: "Cannot Install VMware Server"
date: 2006-11-08
forum: General Help
---

### Post by happy-and-lost on 2006-11-08
I'm trying to install VMware server, but it just keeps coming up with...

```
jo@jo-laptop:~/vmware-server-distrib$ sudo ./vmware-install.pl 
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.


```

I completely uninstalled anything to do with VMware (including residual config files), and it still gives me that! ](*,)

---

### Post by stefe on 2006-11-12
Go to /usr/bin and delete the vmware folder

Then retry

Good luck

Stephen


> **happy-and-lost said:**
> I'm trying to install VMware server, but it just keeps coming up with...

```
jo@jo-laptop:~/vmware-server-distrib$ sudo ./vmware-install.pl 
Password:
A previous installation of VMware software has been detected.

Failure

Execution aborted.


```

I completely uninstalled anything to do with VMware (including residual config files), and it still gives me that! ](*,)

---

### Post by swancott on 2006-11-13
You need to run this script:

/vmware-server-distrib/bin/vmware-uninstall.pl

---

### Post by happy-and-lost on 2006-11-13
Nope, still the same error message.

---

### Post by caaqayuush on 2006-11-15
I am actually getting this problem as well... Any help would be appreciated.

---

### Post by g7kse on 2006-11-15
there is a folder in etc that need removing. Open terminal and type

sudo rm -dr vmware 

That should do it. Or at least it did for me

Cheers

---

### Post by happy-and-lost on 2006-11-15
Ooh! Nearly... now I get...

```
jo@jo-laptop:~$ sudo ./vmware-server-distrib/vmware-install.pl 
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

Unable to copy the source file ./installer/services.sh to the destination file 
/etc/init.d/vmware.

Execution aborted.

```

---

### Post by krotaz on 2006-11-24
well the last error means that you do not have root permissions.

First do a sudo su and then try again.

also you can follow this how-to

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

bye

---

### Post by Kingsley on 2006-11-25
go to /etc and delete the vmware folder.

---

### Post by happy-and-lost on 2006-11-25
The saga continues! Now I get...

```

jo@mithos:~$ cd vmware-server-distrib/
jo@mithos:~/vmware-server-distrib$ sudo sh ./vmware-install.pl 
Password:
./vmware-install.pl: line 8: use: command not found
./vmware-install.pl: line 11: use: command not found
./vmware-install.pl: line 14: my: command not found
./vmware-install.pl: line 15: my: command not found
./vmware-install.pl: line 16: my: command not found
./vmware-install.pl: line 17: my: command not found
./vmware-install.pl: line 18: my: command not found
./vmware-install.pl: line 19: my: command not found
./vmware-install.pl: line 20: my: command not found
./vmware-install.pl: line 21: my: command not found
./vmware-install.pl: line 22: my: command not found
./vmware-install.pl: line 23: my: command not found
./vmware-install.pl: line 24: my: command not found
./vmware-install.pl: line 25: my: command not found
./vmware-install.pl: line 28: my: command not found
./vmware-install.pl: line 31: my: command not found
./vmware-install.pl: line 35: my: command not found
./vmware-install.pl: line 36: my: command not found
./vmware-install.pl: line 37: my: command not found
./vmware-install.pl: line 38: my: command not found
./vmware-install.pl: line 39: my: command not found
./vmware-install.pl: line 40: my: command not found
./vmware-install.pl: line 41: my: command not found
./vmware-install.pl: line 43: my: command not found
./vmware-install.pl: line 44: my: command not found
./vmware-install.pl: line 45: my: command not found
./vmware-install.pl: line 46: my: command not found
./vmware-install.pl: line 47: my: command not found
./vmware-install.pl: line 50: sub: command not found
./vmware-install.pl: line 51: undef: command not found
./vmware-install.pl: line 52: undef: command not found
./vmware-install.pl: line 53: undef: command not found
./vmware-install.pl: line 54: undef: command not found
./vmware-install.pl: line 55: undef: command not found
./vmware-install.pl: line 57: syntax error near unexpected token `INSTALLDB,'
./vmware-install.pl: line 57: `  open(INSTALLDB, '<' . $gInstallerMainDB)'

```

---


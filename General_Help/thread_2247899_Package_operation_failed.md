---
title: "Package operation failed"
date: 2014-10-11
forum: General Help
---

### Post by Roger D on 2014-10-11
Hi

I don't seem to be able to update my installation - Ubuntu 14.04, 64 bit.

Everytime I run the Software Updater I get the message:

Package operation failed
The installation or removal of a software package failed

With all tha talk about the Bash vulnerability this is all a bit worrying.

Can anyone help me get to the bottom of this problem please?

RogerD

---

### Post by kc1di on 2014-10-11
Go to a terminal and type the following commands one at a time:
```
sudo apt-get clean 
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

List any error messages it gives you here.

this has nothing to do with the bash vulnerability.

---

### Post by Trent T on 2014-10-15
Hi all,
This appears to be bug 1279639 on launchpad.net.

I ran the steps above and received the following error messages;

```
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr
/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I then attempted to re-install samba from CLI

```
sudo apt-get install samba4
```

This seemed to generate the same error messages

```
Unknown parameter encountered: "lpq command"
Ignoring unknown parameter "lpq command"
Unknown parameter encountered: "lprm command"
Ignoring unknown parameter "lprm command"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
                                                              
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
username~$ 

```

I tried Update Manager again.

It told me that 'All updates are complete.'

**So possibly, the 3-step process above resolved the bug on my system,** 
although it still resulted in error messages.

Caveats;
Not sure it was necessary to try reinstalling samba4.
I am not sure of the meaning of 'MaxReports' or 'error code (1)'

Thanks Roger D and kc1di !!
Best of luck to all!
Trent T.

My system;
Ubuntu 12.04   32-bit
desktop
RAM: 1.9 GiB
CPU: Intel Celeron CPU  E1200 @ 1.60 GHz x 2

---


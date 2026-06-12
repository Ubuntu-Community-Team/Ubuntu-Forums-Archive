---
title: "cant remove freenx."
date: 2005-07-30
forum: General Help
---

### Post by puccaso on 2005-07-30
i get this ugly error
whats going on 
someone help me!
i cant install anything cos of htis stupid program
i did a nxsetup --unintall -purge
then i went to do apt-get remove freenx, it removed all the other stuff but not freenx.

this is the output

 ```
mahir@jt:~$ screen -D -RR vista
root@jt:/# apt-get -f -m remove freenx
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  freenx
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 139kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 91554 files and directories currently installed.)
Removing freenx ...
dpkg: error processing freenx (--remove):
 subprocess pre-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 freenx
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jt:/#

``` 


helppppppppppppppppppppppp

---

### Post by PeteJ on 2005-10-20
I'm getting exactly the same error.  Any suggestions?

---


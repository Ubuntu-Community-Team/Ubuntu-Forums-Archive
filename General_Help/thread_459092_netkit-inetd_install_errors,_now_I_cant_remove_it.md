---
title: "netkit-inetd install errors, now I cant remove it?"
date: 2007-05-30
forum: General Help
---

### Post by lungdart on 2007-05-30
I'm running ubuntu 7.04, and I am trying to do a PXE/RIS install of Windows 2000 pro to a laptop with no working hard drive, and no working floppy drive. I am following these guides.

[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install](http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install)
[http://oss.netfarm.it/guides/pxe.php](http://oss.netfarm.it/guides/pxe.php)
[http://oss.netfarm.it/guides/ris-linux.php](http://oss.netfarm.it/guides/ris-linux.php)

First of all, when I first installed the netkit-inetd package, there was an error. a post setup error and dpkg returned a 1. (E: Sub-process /usr/bin/dpkg returned an error code (1) )

I ignored it for the most part because when I booted the laptop with PXE, it loaded the ubuntu installation fine (However it has ubuntu and its current owner wants windows back on it. A shame, but she will turn eventually :P )

Now, I was dumping the win2k pro cd over to my hard drive, when my cd rom started spinning and my computer locked up. I took a gander at the cd drive and the molex connecter was shorting itself out on it. I fixed the connect and rebooted.

Since then the laptop can no longer find the tftpd server I have running. It just times out. I figured it might have been due to the inetd error, since I couldnt do a sudo /etc/init.d/inetd restart. I just got no such file errors.

Trying to remove the package gives me this error

```

Removing netkit-inetd ...
/var/lib/dpkg/info/netkit-inetd.prerm: 5: /etc/init.d/inetd: not found
dpkg: error processing netkit-inetd (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Trying to install it says it is at the latest version.

Is there anyway I can force this to be removed so I could install it again to attempt at getting the tftpd server to be reconized?

P.S.: I have tried connecting to my tftpd server with tftp on the same machine using 127.0.0.1, and it still times out. So its not the network or anything, it lies within the server. Also doing a netstat -uap does return a tftp entry.

Anyhelp?

---

### Post by Ufo on 2007-06-08
Hi

 Have you tried

dpkg --force-all --purge netkit-inetd

---

### Post by BlueN1nja on 2007-06-27
I'm getting the same error.

dpkg --force-all --purge netkid-inetd doesn't work:

```

$ sudo dpkg --force-all --purge netkit-inetd

(Reading database ... 132195 files and directories currently installed.)
Removing netkit-inetd ...
/var/lib/dpkg/info/netkit-inetd.prerm: 5: /etc/init.d/inetd: not found
dpkg: error processing netkit-inetd (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 netkit-inetd


```

An apt-get -f install doesn't say there's anything wrong, apt-get install netkit-inetd says it's installed. apt-get remove, however:
```
Removing netkit-inetd ...
/var/lib/dpkg/info/netkit-inetd.prerm: 5: /etc/init.d/inetd: not found
dpkg: error processing netkit-inetd (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 netkit-inetd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---


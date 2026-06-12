---
title: "Problem on locale"
date: 2007-10-02
forum: General Help
---

### Post by satimis on 2007-10-02
Hi folks,


Ubuntu 7.04 server amd64 Host OS
vmware-mui-distrib-1.0.4-56528
vmware-server-distrib-1.0.4-56528


I have been suffering on similar problem, having googling around for 2 days without a solution.


1)
1st problem - on ssh

On an Ubuntu 7.04 desktop running

$ ssh -Y user@server_router_ip rox
password: ```


(process:5576): Gdk-WARNING **: locale not supported by C library

(rox:5576): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```

Remark: rox - a light-weight file manager


$ ssh user@server_router_ip
$ ls
displaying files and directories of the server which indicates server connnected.


On the other way:

On server
$ ssh -Y user@desktop_router_ip rox
it connected with the rox displayed locally.



2)
2nd problem - on VMWare

$ sudo /etc/init.d/httpd.vmware start```

Starting httpd.vmware:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_HK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```


$ locale```

LANG=en_HK.UTF-8
LC_CTYPE="en_HK.UTF-8"
LC_NUMERIC="en_HK.UTF-8"
LC_TIME="en_HK.UTF-8"
LC_COLLATE="en_HK.UTF-8"
LC_MONETARY="en_HK.UTF-8"
LC_MESSAGES="en_HK.UTF-8"
LC_PAPER="en_HK.UTF-8"
LC_NAME="en_HK.UTF-8"
LC_ADDRESS="en_HK.UTF-8"
LC_TELEPHONE="en_HK.UTF-8"
LC_MEASUREMENT="en_HK.UTF-8"
LC_IDENTIFICATION="en_HK.UTF-8"
LC_ALL=

```

$ locale -a```

C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```


$ apt-cache policy language-pack-en```

language-pack-en:
  Installed: 1:7.04+20070601
  Candidate: 1:7.04+20070601
  Version table:
 *** 1:7.04+20070601 0
        500 http://us.archive.ubuntu.com feisty-updates/main Packages
        100 /var/lib/dpkg/status
     1:7.04+20070412 0
        500 http://us.archive.ubuntu.com feisty/main Packages

```

Please advise how to fix the problem.  TIA.


Remark:
Previously I also suffered on locale problem on this box.  I tried to fix it with a new installation of locale resulting in the server crashed.  This is a fresh installation, NOT completed yet.





B.R.
satimis

---

### Post by boogachamp on 2007-10-07
I see something similar using aptitude on my Gutsy install:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by satimis on 2007-10-07
> **boogachamp said:**
> I see something similar using aptitude on my Gutsy install:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Hi boogachamp,


Thanks for your advice.

I think there is nothing to do with locale.  The warning is misleading.

After stopping iptables running on the server, on desktop/workstation run;

$ ssh -X satimis@192.168.0.10 rox

It works.  The remote rox of the server is displayed on desktop locally.


B.R.
satimis

---


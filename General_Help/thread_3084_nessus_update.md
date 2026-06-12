---
title: "nessus update?"
date: 2004-11-03
forum: General Help
---

### Post by lincoln on 2004-11-03
I used synaptic to install nessus and nessusd, but when I run nessus-update-plugins I get an error message telling me that wget is not installed.

If I type in 'wget' it is indeed installed, and if I try to 'apt-get install wget' it tells me I already have the latest version.

Is there any way to update the nessus plugins?

---

### Post by ubuntu-geek on 2004-11-09
To fix this issue:
 Open a terminal window
 sudo nano /usr/sbin/nessus-update-plugins
 
 Search for:
 fetch_cmd="wget"
 
 Change to:
 fetch_cmd="/usr/bin/wget"
 
 That should fix up the issue :)

---

### Post by molvistan on 2004-12-25
when i try to update nessus plugins i get the following error,

-----------------------------------------------------------------------------------------------------------------------
# nessus-update-plugins

--15:35:02--  [http://www.nessus.org/nasl/all-2.0.tar.gz](http://www.nessus.org/nasl/all-2.0.tar.gz)
           => `all-2.0.tar.gz.1'
Resolving [www.nessus.org](www.nessus.org)... 66.240.11.101
Connecting to [www.nessus.org](www.nessus.org)[66.240.11.101]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,521,704 [application/x-tar]

100%[====================================>] 2,521,704     35.00K/s    ETA 00:00

15:36:23 (30.52 KB/s) - `all-2.0.tar.gz.1' saved [2521704/2521704]

**Something went wrong when installing the plugins - uncompressing the plugins archive failed**
-------------------------------------------------------------------------------------------------------------------------


is there a way to get around this.

thanks

---

### Post by cagney on 2005-01-30
[QUOTE=molvistan]when i try to update nessus plugins i get the following error,

-----------------------------------------------------------------------------------------------------------------------
# nessus-update-plugins

--15:35:02--  [http://www.nessus.org/nasl/all-2.0.tar.gz](http://www.nessus.org/nasl/all-2.0.tar.gz)
           => `all-2.0.tar.gz.1'
Resolving [www.nessus.org](www.nessus.org)... 66.240.11.101
Connecting to [www.nessus.org](www.nessus.org)[66.240.11.101]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,521,704 [application/x-tar]

100%[====================================>] 2,521,704     35.00K/s    ETA 00:00

15:36:23 (30.52 KB/s) - `all-2.0.tar.gz.1' saved [2521704/2521704]

**Something went wrong when installing the plugins - uncompressing the plugins archive failed**
-------------------------------------------------------------------------------------------------------------------------


is there a way to get around this.

thanks[/QUOTE]


Change line ~ 250 i /usr/sbin/nessus-update-plugins 
from
$fetch_cmd $fetch_args $proxyopts "$location" > all-2.0.tar.gz
to
$fetch_cmd $fetch_args $proxyopts "$location" 2>&1 > /dev/null &&

This should solve the problem.  8)

---

### Post by eifersucht on 2005-09-30
# nessus-update-plugins

An unknown HTTP error occured (http error code: -1210820602)
Could not retrieve the plugins MD5
Aborting


HELP 
How should i fix this ?

---

### Post by rossellamj on 2005-10-27
I'm having the same problem too, I tried to get the plugins in many ways, tried to register too but it failed. Any idea anybody?:

root@cccnes:/home/rmj# nessus-update-plugins
[8683] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket
Could not retrieve the plugins MD5
Aborting

root@cccnes:/home/rmj# nessus-fetch --plugins
[8686] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket

root@cccnes:/home/rmj# nessus-update-plugins -vv
+ for i in '$opts'
+ case $i in
+ '[' -z y ']'
+ tar=-xvf
+ '[' '!' -d /var/lib/nessus/plugins ']'
++ pwd
+ cwd=/home/rmj
+ tmpdir=
+ test -z ''
+ tmpdir=
+ test -z ''
+ tmpdir=/tmp
+ mkdir -m 0700 /tmp/nessus-update-plugins-8687
+ cd /tmp/nessus-update-plugins-8687
+ /usr/bin/nessus-fetch --plugins-md5
[8693] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/80=1;
']: Socket operation on non-socket
Could not open connection to [www.nessus.org](www.nessus.org) - Socket operation on non-socket
+ echo 'Could not retrieve the plugins MD5'
Could not retrieve the plugins MD5
+ echo Aborting
Aborting
+ exit 1

root@cccnes:/home/rmj# nessus-fetch --register 8B77-742F-65BE-277F-83E7
[8694] plug_set_key:internal_send(0)['3 /tmp/ConnectTimeout/TCP/443=1;
']: Socket operation on non-socket

---

### Post by rossellamj on 2005-10-27
[QUOTE=ubuntu-geek]To fix this issue:
 Open a terminal window
 sudo nano /usr/sbin/nessus-update-plugins
 
 Search for:
 fetch_cmd="wget"
 
 Change to:
 fetch_cmd="/usr/bin/wget"
 
 That should fix up the issue :)[/QUOTE]
Those lines don't exist in my file. We're running the Ubuntu Nessus packages. Would we need to do the basic install instead? Any other ideas? Thanks.

---

### Post by Carpe Noctem on 2007-05-15
In Terminal type ¨sudo nessus-update-plugins¨ without quotes, 
wait, done!\\:D/

---

### Post by fakie_flip on 2007-05-21
I have nessus-update-plugins and nessus-update-plugins-gpl. What's the difference? Is there a guide to using Nessus in Ubuntu? I am searching these forums for one, but have not found one yet.

---

### Post by buhrmj on 2008-05-08
In order for nessus-update-plugins to work you need to register your scanner at [http://www.nessus.org/plugins/index.php?view=register-info](http://www.nessus.org/plugins/index.php?view=register-info). I was getting the unknown http error message others listed above until I registered.

---


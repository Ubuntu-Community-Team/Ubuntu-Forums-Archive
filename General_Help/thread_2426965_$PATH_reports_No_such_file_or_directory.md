---
title: "$PATH reports: No such file or directory"
date: 2019-09-16
forum: General Help
---

### Post by wardenburg on 2019-09-16
hey everyone,

having a bit of an issue with my ubuntu currently and even though I have the suspicion that I'm close to a solution I'm not profficient enough in linux to solve it.

Running a Ubuntu 18.04 fresh install, issue is that my dkpg gives install-info errors when I update/install packages, i'll first describe the main issue I'm facing:


[COLOR=#242729][FONT=Arial]When I run any apt-get update/install/remove command after the initial gathering of the package I get the following message (no matter what I try to run/get):
[/FONT][/COLOR]
> Setting up install-info (6.5.0.dfsg.1-2) ...
/usr/sbin/update-info-dir: 1: /etc/environment: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: not found
dpkg: error processing package install-info (--configure):
 installed install-info package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)


[COLOR=#242729][FONT=Arial]I suspect it involves something in my /etc/environment file, but I cannot find anything off with it; my hope is someone here can see the problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Heres my /etc/environment file;

[/FONT][/COLOR]
> $PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
$linux_ip = 192.168.100.38
$linux_hostname = "vmwbpap03"
$domain = "intern.domainname.nl"
$ad_ip = 192.168.1.2
$ad_hostname = "Hostname AD"


The current main problem i see is that when I Type $PATH in the console I get the following message:

> root@vmwbpapp03:~# $PATH
-bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin: [COLOR=#ff0000]No such file or directory[/COLOR]


--

Any idea how to solve this problem? 

Any and all suggestions on how to proceed/solve this would be greatly appreciated

---

### Post by yetimon_64 on 2019-09-16
> **wardenburg said:**
> ...The current main problem i see is that when I Type $PATH in the console I get the following message:...

Any idea how to solve this problem? 

Any and all suggestions on how to proceed/solve this would be greatly appreciated

To get rid of the bash error message and show the path use the command...
```
echo $PATH
```
Just expanding the system path as a command is why you are  getting the "-bash: ... [COLOR=#ff0000]No such file or directory[/COLOR]" error. 

Try echoing the system path with the command above to see the path.

I'm not particularly sure about the original dpkg aspect of your post, await further help on that. 

Regards, yeti.

---

### Post by dragonfly41 on 2019-09-16
[COLOR=#000000][I]:/snap/bin=/

The = sign looks odd to me in your $PATH[/I][/COLOR]

---

### Post by spjackson on 2019-09-16
> **wardenburg said:**
> 
[FONT=Arial]I suspect it involves something in my /etc/environment file, but I cannot find anything off with it; my hope is someone here can see the problem.[/FONT]
[COLOR=#242729][FONT=Arial]Heres my /etc/environment file;
[/FONT][/COLOR]```
$PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
$linux_ip = 192.168.100.38
$linux_hostname = "vmwbpap03"
$domain = "intern.domainname.nl"
$ad_ip = 192.168.1.2
$ad_hostname = "Hostname AD"                      

```

If you really have a $ at the start of each line, then that's your problem. These should not be there.

---

### Post by wardenburg on 2019-09-17
> **spjackson said:**
> If you really have a $ at the start of each line, then that's your problem. These should not be there.

Hey There spjackson,

First off thanks for the reply- the $ are indeed there (I reckon these were placed there following this assp guide I followed, I dont consider myself an expert linux user to do these changes without a guide)

I attempted to remove them resulting in;

> 
[COLOR=#000000]*PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"*[/COLOR]
[COLOR=#000000]*linux_ip = 192.168.100.38*[/COLOR]
[COLOR=#000000]*linux_hostname = "vmwbpap03"*[/COLOR]
[COLOR=#000000]*domain = "intern.domainname.nl"*[/COLOR]
[COLOR=#000000]*ad_ip = 192.168.1.2*[/COLOR]
[COLOR=#000000][I]ad_hostname = "Hostname AD"
[/I][/COLOR] 

I'm attempting to install sqlite3 with the 'apt-get install sqlite3' command. resulting in the following error:

> Preconfiguring packages ...
Setting up install-info (6.5.0.dfsg.1-2) ...
/usr/sbin/update-info-dir: 2: /etc/environment: linux_ip: not found
dpkg: error processing package install-info (--configure):
 installed install-info package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)


Noting the linux_ip error I tried the following environment:

> 
[COLOR=#000000]*PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"*[/COLOR]


which resulted in the following error:

> Preparing to unpack .../sqlite3_3.22.0-1ubuntu0.1_amd64.deb ...Unpacking sqlite3 (3.22.0-1ubuntu0.1) ...
Setting up sqlite3 (3.22.0-1ubuntu0.1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
W: APT had planned for dpkg to do more than it reported back (5 vs 9).
   Affected packages: install-info:amd64


So I suppose that the problem has something to do with the environment but I'm at a loss where to begin with how to solve this.

---

### Post by SeijiSensei on 2019-09-17
My /etc/environment just includes the PATH.  Are those other items designed to join a Microsoft Active Directory network?  I suggest you dump them until you get everything working correctly.

/etc/environment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

---

### Post by spjackson on 2019-09-17
> **wardenburg said:**
> First off thanks for the reply- the $ are indeed there (I reckon these were placed there following this assp guide I followed, I dont consider myself an expert linux user to do these changes without a guide)

I attempted to remove them resulting in;
```

[COLOR=#000000]*PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"*[/COLOR]
[COLOR=#000000]*linux_ip = 192.168.100.38*[/COLOR]
[COLOR=#000000]*linux_hostname = "vmwbpap03"*[/COLOR]
[COLOR=#000000]*domain = "intern.domainname.nl"*[/COLOR]
[COLOR=#000000]*ad_ip = 192.168.1.2*[/COLOR]
[COLOR=#000000][I]ad_hostname = "Hostname AD"
[/I][/COLOR]
```
 I'm attempting to install sqlite3 with the 'apt-get install sqlite3' command. resulting in the following error:
```

Preconfiguring packages ...
Setting up install-info (6.5.0.dfsg.1-2) ...
/usr/sbin/update-info-dir: 2: /etc/environment: linux_ip: not found

```
Noting the linux_ip error I tried the following environment:

man 5 environment says "The file must consist of simple NAME=VALUE pairs on separate lines." I don't think you can have the spaces before and after the =, just as with variable assignment in the shell. Sorry I missed this originally.
In a shell:
```

[COLOR=#000000][I]linux_ip=192.168.100.38
echo $linux_ip
[COLOR=#000000]*192.168.100.38*[/COLOR]
[/I][/COLOR]
```[COLOR=#000000][I]
But...
[/I][/COLOR]```

[COLOR=#000000][I]linux_ip = 192.168.100.38
[/I][/COLOR]bash: linux_ip: command not found

```

---

### Post by wardenburg on 2019-09-18
> **SeijiSensei said:**
> My /etc/environment just includes the PATH. Are those other items designed to join a Microsoft Active Directory network? I suggest you dump them until you get everything working correctly.

/etc/environment
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```

I think this was the idea yeah, It might've been parts of my attempt to join an AD before I found the realm join command 

> **spjackson said:**
> man 5 environment says "The file must consist of simple NAME=VALUE pairs on separate lines." I don't think you can have the spaces before and after the =, just as with variable assignment in the shell. Sorry I missed this originally.
In a shell:
```

[COLOR=#000000][I]linux_ip=192.168.100.38
echo $linux_ip
[COLOR=#000000]*192.168.100.38*[/COLOR]
[/I][/COLOR]
```[COLOR=#000000][I]
But...
[/I][/COLOR]```

[COLOR=#000000][I]linux_ip = 192.168.100.38
[/I][/COLOR]bash: linux_ip: command not found

```

[COLOR=#00ff00][SIZE=4]This was the solution[/SIZE][/COLOR], Learning a lot here fellas. (It works now and I couldn't be happier) :KS

Thank you so much for the help,

---


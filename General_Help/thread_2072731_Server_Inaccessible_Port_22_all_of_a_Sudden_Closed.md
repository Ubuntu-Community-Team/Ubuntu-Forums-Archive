---
title: "Server Inaccessible: Port 22 all of a Sudden Closed"
date: 2012-10-18
forum: General Help
---

### Post by Thresholder on 2012-10-18
Hello,

I have 2 Kimsufi 2G servers with a Ubuntu Desktop 12.04 distro.

All of a sudden one of the servers has become inaccessible and support told me that port 22 on secure shell is closed.

They also told me that I have to sort it myself through secure mode but, to be honest, I don't know  exactly what to do.

I didn't install, update or modify anything on the server so have no clue why all of a sudden it's inaccessible.
I can access the other server without any problem.

So far, on some friends' suggestions, I ran the following commands although I cannot read the results:

root@rescue:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@rescue:~# Chain INPUT (policy ACCEPT)
-bash: syntax error near unexpected token `('
root@rescue:~# target     prot opt source               destination
-bash: target: command not found
root@rescue:~#
root@rescue:~# Chain FORWARD (policy ACCEPT)
-bash: syntax error near unexpected token `('
root@rescue:~# target     prot opt source               destination
-bash: target: command not found
root@rescue:~#
root@rescue:~# Chain OUTPUT (policy ACCEPT)
-bash: syntax error near unexpected token `('
root@rescue:~# target     prot opt source               destination
-bash: target: command not found
root@rescue:~# root@rescue:~#
-bash: root@rescue:~#: command not found
root@rescue:~#

root@rescue:~# sudo apt-get openssh-server openssh-client
E: Invalid operation openssh-server
root@rescue:~#

Any help appreciated as it's almost a week that I cannot access the server.

Thank you

---

### Post by Insomn1a on 2012-10-18
to install openssh-server you need to use sudo apt-get *_install_* openssh-server.

if it says it is already installed, use:
sudo apt-get install --reinstall openssh-server


you won't need openssh client as you probably won't be terminaling to another server from that server. just openssh server is needed to access that server via terminal.

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> to install openssh-server you need to use sudo apt-get *_install_* openssh-server.

if it says it is already installed, use:
sudo apt-get install --reinstall openssh-server


you won't need openssh client as you probably won't be terminaling to another server from that server. just openssh server is needed to access that server via terminal.

Hello Insomn1a, thank you for your reply.

I got this:

root@rescue:~# sudo apt-get install openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

I don't understand the results, do you or anyone else please?

I also don't understand this part:
*"you won't need openssh client as you probably won't be terminaling to  another server from that server. just openssh server is needed to access  that server via terminal."*

What exactly are you asking me to do?

Thank you :)

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Hello Insomn1a, thank you for your reply.

I got this:

root@rescue:~# sudo apt-get install openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

I don't understand the results, do you or anyone else please?

I also don't understand this part:
*"you won't need openssh client as you probably won't be terminaling to  another server from that server. just openssh server is needed to access  that server via terminal."*

What exactly are you asking me to do?

Thank you :)

What i am saying is that if you are wanting to connect to a server via SSH, openssh client installed on said server is not required, the only requirement for ssh to work on a server is openssh-server

try doing this in terminal

sudo apt-get update
sudo apt-get upgrade

then try reinstall openssh server


sudo apt-get install --reinstall openssh-server

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> What i am saying is that if you are wanting to connect to a server via SSH, openssh client installed on said server is not required, the only requirement for ssh to work on a server is openssh-server

try doing this in terminal

sudo apt-get update
sudo apt-get upgrade

then try reinstall openssh server


sudo apt-get install --reinstall openssh-server

Gotcha thanks for the clarification.

I tried just updating and I get this:

root@rescue:~# sudo apt-get update
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze Release.gpg
Ign [http://hwraid.le-vert.net/debian/](http://hwraid.le-vert.net/debian/) squeeze/main Translation-en
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze Release
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages/DiffIndex
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
Err [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/hwraid.le-vert.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system)
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates Release.gpg
Ign [http://security.debian.org/](http://security.debian.org/) squeeze/updates/main Translation-en
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates Release
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources/DiffIndex
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages/DiffIndex
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze Release.gpg
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/contrib Translation-en
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/main Translation-en
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/non-free Translation-en
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze Release
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_source_Sources - open (30: Read-only file system) [IP: 91.121.124.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_contrib_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.124.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_non-free_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
Err [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_source_Sources - open (30: Read-only file system) [IP: 195.20.242.89 80]
Err [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_binary-i386_Packages - open (30: Read-only file system) [IP: 212.211.132.32 80]
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://hwraid.le-vert.net/debian/dists/squeeze/main/binary-i386/Packages.gz](http://hwraid.le-vert.net/debian/dists/squeeze/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/hwraid.le-vert.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system)

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/main/source/Sources.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_source_Sources - open (30: Read-only file system) [IP: 91.121.124.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/main/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/contrib/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/contrib/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_contrib_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.124.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/non-free/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/non-free/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_non-free_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/source/Sources.gz](http://security.debian.org/dists/squeeze/updates/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_source_Sources - open (30: Read-only file system) [IP: 195.20.242.89 80]

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/binary-i386/Packages.gz](http://security.debian.org/dists/squeeze/updates/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_binary-i386_Packages - open (30: Read-only file system) [IP: 212.211.132.32 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock



root@rescue:~# sudo apt-get upgrade
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

root@rescue:~# sudo apt-get install --reinstall openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

P.s. I would like to paste all the results in those scrollable windows but have no clue how :)

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Gotcha thanks for the clarification.

I tried just updating and I get this:

root@rescue:~# sudo apt-get update
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze Release.gpg
Ign [http://hwraid.le-vert.net/debian/](http://hwraid.le-vert.net/debian/) squeeze/main Translation-en
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze Release
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages/DiffIndex
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
Ign [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
Err [http://hwraid.le-vert.net](http://hwraid.le-vert.net) squeeze/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/hwraid.le-vert.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system)
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates Release.gpg
Ign [http://security.debian.org/](http://security.debian.org/) squeeze/updates/main Translation-en
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates Release
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources/DiffIndex
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages/DiffIndex
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze Release.gpg
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/contrib Translation-en
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/main Translation-en
Ign [http://debian.mirrors.ovh.net/debian/](http://debian.mirrors.ovh.net/debian/) squeeze/non-free Translation-en
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze Release
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages/DiffIndex
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
Ign [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main Sources
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_source_Sources - open (30: Read-only file system) [IP: 91.121.124.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/contrib i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_contrib_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.124.139 80]
Err [http://debian.mirrors.ovh.net](http://debian.mirrors.ovh.net) squeeze/non-free i386 Packages
  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_non-free_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
Ign [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
Err [http://security.debian.org](http://security.debian.org) squeeze/updates/main Sources
  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_source_Sources - open (30: Read-only file system) [IP: 195.20.242.89 80]
Err [http://security.debian.org](http://security.debian.org) squeeze/updates/main i386 Packages
  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_binary-i386_Packages - open (30: Read-only file system) [IP: 212.211.132.32 80]
W: Not using locking for read only lock file /var/lib/apt/lists/lock
W: Failed to fetch [http://hwraid.le-vert.net/debian/dists/squeeze/main/binary-i386/Packages.gz](http://hwraid.le-vert.net/debian/dists/squeeze/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/hwraid.le-vert.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system)

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/main/source/Sources.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_source_Sources - open (30: Read-only file system) [IP: 91.121.124.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/main/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_main_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/contrib/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/contrib/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_contrib_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.124.139 80]

W: Failed to fetch [http://debian.mirrors.ovh.net/debian/dists/squeeze/non-free/binary-i386/Packages.gz](http://debian.mirrors.ovh.net/debian/dists/squeeze/non-free/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/debian.mirrors.ovh.net_debian_dists_squeeze_non-free_binary-i386_Packages - open (30: Read-only file system) [IP: 91.121.125.139 80]

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/source/Sources.gz](http://security.debian.org/dists/squeeze/updates/main/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_source_Sources - open (30: Read-only file system) [IP: 195.20.242.89 80]

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/binary-i386/Packages.gz](http://security.debian.org/dists/squeeze/updates/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/security.debian.org_dists_squeeze_updates_main_binary-i386_Packages - open (30: Read-only file system) [IP: 212.211.132.32 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
W: Not using locking for read only lock file /var/lib/dpkg/lock



root@rescue:~# sudo apt-get upgrade
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

root@rescue:~# sudo apt-get install --reinstall openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

P.s. I would like to paste all the results in those scrollable windows but have no clue how :)

wait a second, are you in recovery mode? reboot that server.

sudo shutdown -g0 -y -r

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> wait a second, are you in recovery mode? reboot that server.

sudo shutdown -g0 -y -r

Yes I think I mentioned it at the beginning.
They call it rescue mode.

Before I reboot there are also some tests that I can run (I have data in the servers) as outlined here:
[http://help.ovh.co.uk/RescueMode](http://help.ovh.co.uk/RescueMode)
Anything you might want me to test before I reboot?

Thank you

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Yes I think I mentioned it at the beginning.
They call it rescue mode.

Before I reboot there are also some tests that I can run (I have data in the servers) as outlined here:
[http://help.ovh.co.uk/RescueMode](http://help.ovh.co.uk/RescueMode)
Anything you might want me to test before I reboot?

Thank you

the reason we cannot reinstall openssh is because by default some of the file system is read only in recovery console, at least with your system it is, what we need to do is get out of the recovery console and boot into your normal operating system.

If you have physical access to these servers, then perform the following:

sudo shutdown -g0 -y -r

whenever the server fully reboots and is at a login prompt, login using your credentials.

after logging in, do the following:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall openssh-server

then test ssh connection to the server, if you still cannot get a connection to the server then my next question is:

do you have any firewalls installed or running on these servers?

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> the reason we cannot reinstall openssh is because by default some of the file system is read only in recovery console, at least with your system it is, what we need to do is get out of the recovery console and boot into your normal operating system.

If you have physical access to these servers, then perform the following:

sudo shutdown -g0 -y -r

whenever the server fully reboots and is at a login prompt, login using your credentials.

after logging in, do the following:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall openssh-server

then test ssh connection to the server, if you still cannot get a connection to the server then my next question is:

do you have any firewalls installed or running on these servers?

Hi Insomn1a,

I don't think that is actually possible since the only way I can actually log into the server is through rescue mode and I do not have physical access to the servers as they are in a server farm in another country.

Any other suggestions? :)

Thank you

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Hi Insomn1a,

I don't think that is actually possible since the only way I can actually log into the server is through rescue mode and I do not have physical access to the servers as they are in a server farm in another country.

Any other suggestions? :)

Thank you

in the rescue console, try 

mount -o rw,remount /

then try the previous commands i had mentioned

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall openssh-server

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> in the rescue console, try 

mount -o rw,remount /

then try the previous commands i had mentioned

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall openssh-server

No luck unfortunately: I got all those failed messages I pasted before.

Any further suggestion appreciated.

Thank you

---

### Post by Insomn1a on 2012-10-18
If you already have ssh installed, try 

sudo service ssh start

if that doesnt work

sudo /etc/init.d/ssh start

then see if you can connect to it, other then that im running out of idea's and we might have to wait for someone else to post.

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> If you already have ssh installed, try 

sudo service ssh start

if that doesnt work

sudo /etc/init.d/ssh start

then see if you can connect to it, other then that im running out of idea's and we might have to wait for someone else to post.

root@rescue:~# sudo service ssh start
Starting OpenBSD Secure Shell server: sshd.
root@rescue:~#

Than, after changing in the server manager to regular mode,  I just wrote sudo reboot and the server rebooted (it never worked before so I had to hard reboot it).

Unfortunately when I try to connect via normal method I still get: 
Network error: connection refused.

What are your ideas left? :)

Many thanks

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> root@rescue:~# sudo service ssh start
Starting OpenBSD Secure Shell server: sshd.
root@rescue:~#

Than, after changing in the server manager to regular mode,  I just wrote sudo reboot and the server rebooted (it never worked before so I had to hard reboot it).

Unfortunately when I try to connect via normal method I still get: 
Network error: connection refused.

What are your ideas left? :)

Many thanks


so you can't run any commands whatsoever in regular mode?

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> so you can't run any commands whatsoever in regular mode?

No because I cannot even input the credentials to access the server. :(

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> No because I cannot even input the credentials to access the server. :(

ok, so what method are you using to access the server right now if ssh is not working.

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> ok, so what method are you using to access the server right now if ssh is not working.

I don't access it in fact; that's the all point of my post.

I only manage to access it when I reboot it in rescue mode.

Thank you.

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> I don't access it in fact; that's the all point of my post.

I only manage to access it when I reboot it in rescue mode.

Thank you.

ok, but if the server is in a datacenter and you can't physically access the server, how are you rebooting it?

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> ok, but if the server is in a datacenter and you can't physically access the server, how are you rebooting it?

There is a web manager that lets me do some things like reinstalling OS and switching from regular mode to rescue mode.

[http://help.ovh.co.uk/RescueMode](http://help.ovh.co.uk/RescueMode)

Thank you

---

### Post by Insomn1a on 2012-10-18
Try the following:

Sudo nano /etc/init.d/autorunssh.sh

in that window, put:

> sudo service ssh start


press Ctrl + x 
then y
then enter

then in console type sudo chmod +x /etc/init.d/autorunssh.sh

then use the following command to update the startup:

> sudo update-rc.d autorunssh.sh defaults

then try and reboot into regular mode.

If it is still not allowing you to connect VIA ssh, then look at the link below:

[http://blog.roberthallam.org/2010/06/sshd-not-running-at-startup/](http://blog.roberthallam.org/2010/06/sshd-not-running-at-startup/)

---

### Post by Insomn1a on 2012-10-18
Also, I followed what the individual was saying on the link at the bottom of my previous post, and with the version of openssh-server that is installed on my 12.04, instead of listenserver its listen address, you should see listenaddress at the top of the sshd config file, you just need to delete the # at the beginning of the line

Before
> 
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
**_#_**ListenAddress 0.0.0.0


After
> 
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> Also, I followed what the individual was saying on the link at the bottom of my previous post, and with the version of openssh-server that is installed on my 12.04, instead of listenserver its listen address, you should see listenaddress at the top of the sshd config file, you just need to delete the # at the beginning of the line

Before


After

Hi Insomn1a,

I just finished running your scripts in the previous post and still it didn't work.

At which step will I find this # to delete please?

Thank you.

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Hi Insomn1a,

I just finished running your scripts in the previous post and still it didn't work.

At which step will I find this # to delete please?

Thank you.

sudo nano /etc/ssh/sshd_config

at the top of that file you will see #listenserver 0.0.0.0

remove the # so it looks like the listenaddress line in the "after" quote in my last post, and save the file, if you can. then reboot.

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> sudo nano /etc/ssh/sshd_config

at the top of that file you will see #listenserver 0.0.0.0

remove the # so it looks like the listenaddress line in the "after" quote in my last post, and save the file, if you can. then reboot.

Hi Insomn1a,

In the nano file I do not have #listenserver 0.0.0.0 or anything else for that matter.

Also since I copied "sudo service ssh start" in nano the first time why I didn't find it there?
I am sure I saved the file the first time.

Anyway after the last step I get this output:

root@rescue:~# sudo update-rc.d autorunssh.sh defaults
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'S24ovh.sh' missing LSB tags and overrides
insserv: warning: script 'S21rescueInterface.pl' missing LSB tags and overrides
insserv: warning: script 'autorunssh.sh' missing LSB tags and overrides
insserv: warning: script 'ovh.sh' missing LSB tags and overrides
insserv: warning: script 'screen_it_for_me' missing LSB tags and overrides
insserv: warning: script 'rescueInterface.pl' missing LSB tags and overrides
unable to write to /var/lib/update-rc.d/autorunssh.sh.new at /usr/sbin/update-rc.d line 59.
root@rescue:~#


Thank you

---

### Post by Insomn1a on 2012-10-18
> **Thresholder said:**
> Hi Insomn1a,

In the nano file I do not have #listenserver 0.0.0.0 or anything else for that matter.

Also since I copied "sudo service ssh start" in nano the first time why I didn't find it there?
I am sure I saved the file the first time.

Anyway after the last step I get this output:

root@rescue:~# sudo update-rc.d autorunssh.sh defaults
update-rc.d: using dependency based boot sequencing
insserv: warning: script 'S24ovh.sh' missing LSB tags and overrides
insserv: warning: script 'S21rescueInterface.pl' missing LSB tags and overrides
insserv: warning: script 'autorunssh.sh' missing LSB tags and overrides
insserv: warning: script 'ovh.sh' missing LSB tags and overrides
insserv: warning: script 'screen_it_for_me' missing LSB tags and overrides
insserv: warning: script 'rescueInterface.pl' missing LSB tags and overrides
unable to write to /var/lib/update-rc.d/autorunssh.sh.new at /usr/sbin/update-rc.d line 59.
root@rescue:~#


Thank you


Ok, sort of running out of idea's lol. 

since we are rebooting, i don't believe that your file system is remounting with write cababilities.

So access the recovery console and first thing you do is remount the file system with write priviledges

so before doing anything make sure this command is run whenever you hit the recovery console:

mount -o remount,rw /

give me the output, if any of this command as well, after running that, I posted the same thing earlier, but try the following:

apt-get remove openssh-server
apt-get install openssh-server

you might want to also try installing telnet temporarily to see if you get connection to the server that way:

apt-get install telnetd

[http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)
This is instructions for access a server via telnet.


also, give me the outputs of these commands

netstat -an | grep LISTEN | grep ":23"
netstat -an | grep LISTEN | grep ":22"


also since this is ubuntu desktop, are you able to access them via VNC or anything like that?

---

### Post by Thresholder on 2012-10-18
> **Insomn1a said:**
> Ok, sort of running out of idea's lol. 

since we are rebooting, i don't believe that your file system is remounting with write cababilities.

So access the recovery console and first thing you do is remount the file system with write priviledges

so before doing anything make sure this command is run whenever you hit the recovery console:

mount -o remount,rw /

give me the output, if any of this command as well, after running that, I posted the same thing earlier, but try the following:

apt-get remove openssh-server
apt-get install openssh-server

you might want to also try installing telnet temporarily to see if you get connection to the server that way:

apt-get install telnetd

[http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)
This is instructions for access a server via telnet.


also, give me the outputs of these commands

netstat -an | grep LISTEN | grep ":23"
netstat -an | grep LISTEN | grep ":22"


also since this is ubuntu desktop, are you able to access them via VNC or anything like that?

Hey no worries I really appreciate all your help.

Did you have a look at the ovh tutorial I posted earlier on?
There is some commands that involve mounting: [http://help.ovh.co.uk/RescueMode](http://help.ovh.co.uk/RescueMode)

Anyway here is the output:

root@rescue:~# mount -o remount,rw /
root@rescue:~# apt-get remove openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

root@rescue:~# apt-get install telnetd
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

root@rescue:~# netstat -an | grep LISTEN | grep ":23"
root@rescue:~#
root@rescue:~# netstat -an | grep LISTEN | grep ":22"
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
root@rescue:~#

Any good results?
I hope so :)

Thank you

P.s. No I cannot access the server through vnc or similar

---

### Post by Insomn1a on 2012-10-18
Ok, so that last netstat you sent me tells me that your server is currently listening on port 22 for ssh, so as of right now you should be able to ssh to it, but whenever your server is in regular mode you cannot access via SSH.

try this, its a shot in the dark but hopefully it will work:

If you haven't rebooted the server yet, then you won't need to do this, but if you have, perform the mounting operation when you first get to the console.

mount -o remount,rw /

Then once you do that, type

sudo nano /etc/init.d/ssh

add the $network string after #required start entry like the other ones are listed

[IMG]https://lh4.googleusercontent.com/-p7VxnzpQnOM/UIC5qjVhkPI/AAAAAAAABp0/s1u9l25-YG0/s837/sshfile.png[/IMG]


also, I accessed one of my servers and rebooted it into recovery mode and tested what i told you, Here are some screenshots

[IMG]https://lh4.googleusercontent.com/-WXMzO3DNFjM/UIC0eY8uiKI/AAAAAAAABpE/tpKp2Hk88FU/s950/recovery.png[/IMG]

Looking at this screenshot you can see that I tried to run an apt-get command before running the mount, and it didnt work, but after doing the mount command it did it just told me that it was already installed,

so what your telling me, is that your doing exactly what is shown in that screenshot and its still locked?

If that is the case, the only thing I can possible think of, is that you aren't really booting into the recovery console on the server, your botting into a read only ISO or CD media that has recovery console on it.

The main thing that bothers me, is that it says root@rescue, which makes me think of ubuntu rescue remix or something along the lines of that, it should say root@yourserverhostname

next time your at the root prompt, try typing exit, and see if it gives you a menu entry

---

### Post by Thresholder on 2012-10-19
> **Insomn1a said:**
> Ok, so that last netstat you sent me tells me that your server is currently listening on port 22 for ssh, so as of right now you should be able to ssh to it, but whenever your server is in regular mode you cannot access via SSH.

try this, its a shot in the dark but hopefully it will work:

If you haven't rebooted the server yet, then you won't need to do this, but if you have, perform the mounting operation when you first get to the console.

mount -o remount,rw /

Then once you do that, type

sudo nano /etc/init.d/ssh

add the $network string after #required start entry like the other ones are listed

[IMG]https://lh4.googleusercontent.com/-p7VxnzpQnOM/UIC5qjVhkPI/AAAAAAAABp0/s1u9l25-YG0/s837/sshfile.png[/IMG]


also, I accessed one of my servers and rebooted it into recovery mode and tested what i told you, Here are some screenshots

[IMG]https://lh4.googleusercontent.com/-WXMzO3DNFjM/UIC0eY8uiKI/AAAAAAAABpE/tpKp2Hk88FU/s950/recovery.png[/IMG]

Looking at this screenshot you can see that I tried to run an apt-get command before running the mount, and it didnt work, but after doing the mount command it did it just told me that it was already installed,

so what your telling me, is that your doing exactly what is shown in that screenshot and its still locked?

If that is the case, the only thing I can possible think of, is that you aren't really booting into the recovery console on the server, your botting into a read only ISO or CD media that has recovery console on it.

The main thing that bothers me, is that it says root@rescue, which makes me think of ubuntu rescue remix or something along the lines of that, it should say root@yourserverhostname

next time your at the root prompt, try typing exit, and see if it gives you a menu entry

Hey Insomn1a.

In rescue mode I managed to add "the $network string after #required start entry".

This is the output:

root@rescue:~# mount -o remount,rw /
root@rescue:~# sudo nano /etc/init.d/ssh
root@rescue:~# sudo apt-get install openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~# mount -o remount,rw /
root@rescue:~# sudo apt-get install openssh-server
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
root@rescue:~#

You can see that even with mounting I cannot install the ssh server.

When I typed exit in putty it just closes.

Thank you

---

### Post by davidryderuk on 2012-10-19
Hi,
Reading the documentation you linked to, it seems like 'Rescue Mode' is a different copy of Linux running on the same machine (like a LiveCD or an External Disk). 

The files you want are on a different partition which probably isn't mounted by default. If you list the partitions available in rescue mode it might be clearer where the normal version of Linux is located.

```
fdisk -l
```

Once you identify the Linux partition you can mount it in the /mnt/ directory, and check the logs at /mnt/var/logs/* for clues.

Good Luck.

---

### Post by Insomn1a on 2012-10-19
> **davidryderuk said:**
> Hi,
Reading the documentation you linked to, it seems like 'Rescue Mode' is a different copy of Linux running on the same machine (like a LiveCD or an External Disk). 

The files you want are on a different partition which probably isn't mounted by default. If you list the partitions available in rescue mode it might be clearer where the normal version of Linux is located.

```
fdisk -l
```

Once you identify the Linux partition you can mount it in the /mnt/ directory, and check the logs at /mnt/var/logs/* for clues.

Good Luck.

yea after going through all this, it sounds like we are trying to gain write access to some sort of locked media, CD/DVD/etc. 

Its wierd, I'm pretty much at the depth of my knowledge regarding this, if anyone else has any idea's please feel free to post.

---

### Post by Thresholder on 2012-10-20
Hello guys and thank you to both of you for the help.

Yesterday a friend accessed my server and tried to fix the issue.

He mounted the correct drives\partitions with these commands:

 [FONT=&quot]mount /dev/sda1 /mnt/[/FONT]
  [FONT=&quot]mount /dev/sda2 /mnt/home[/FONT]
  [FONT=&quot]mount -o remount,rw /[/FONT]
  [FONT=&quot]mount --bind /proc /mnt/proc[/FONT]
    [FONT=&quot]chroot /mnt/[/FONT]
  
 [FONT=&quot]He checked the SSH log (there might have been some hacking attempts he wasn't sure if successful), backed up the ~/.ssh directory and removed it to allow it to configure itself again.[/FONT]
  [FONT=&quot]He then set the SSH settings to the same of his working server uncommenting a single line in /etc/ssh/sshd_config[/FONT]
     
Than he reinstalled Openssh but unfortunately this created another problem that stucks the server in reboot with the following log: "  [FONT=&quot]failed to create pty - disabling logging for job.[/FONT][FONT=&quot]A restart on the standard OVH kernel ('netboot') does not[/FONT]
  [FONT=&quot]correct the[/FONT][FONT=&quot] situation.[/FONT]"


He told me that there is a "known bug in upstart" that he tried to fix following this tutorial:
 [FONT=&quot][SIZE=2][http://askubuntu.com/questions/126779/why-do-i-get-init-failed-to-create-pty-errors-on-boot](http://askubuntu.com/questions/126779/why-do-i-get-init-failed-to-create-pty-errors-on-boot)[/SIZE][/FONT]
  
Unfortunately his fix didn't work so now I cannot even check if the openssh problem is fixed because when I reboot in regular mode the server gets stuck.
I can still access it in recovery mode though.

Anyone who has any further suggestion always much appreciated.

Thank you

---


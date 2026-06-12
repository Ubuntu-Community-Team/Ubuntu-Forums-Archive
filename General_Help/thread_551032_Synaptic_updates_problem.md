---
title: "Synaptic updates problem"
date: 2007-09-14
forum: General Help
---

### Post by KiwiDalang on 2007-09-14
I have two machines running Feisty x86-64. One is working fine the other throws this

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

on everything it wants to update. It does this for all repositories, not just the NZ one.

Both machines have Synaptic and network set up the same as far as I can tell, but the laptop also has a provision for wireless networking that I don't use.

---

### Post by tszanon on 2007-09-14
> **KiwiDalang said:**
> I have two machines running Feisty x86-64. One is working fine the other throws this

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_amd64.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.16-2ubuntu0.1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

on everything it wants to update. It does this for all repositories, not just the NZ one.

Both machines have Synaptic and network set up the same as far as I can tell, but the laptop also has a provision for wireless networking that I don't use.
It seems that nz.archive.ubuntu.com is pointing to localhost (127.0.0.1). I really doubt it may have happened, but please, what's your /etc/hosts file?
```
cat /etc/hosts
```

---

### Post by KiwiDalang on 2007-09-14
Both machines seem to be exactly the same

sue@sue2:/etc$ cat hosts
127.0.0.1 localhost.localdomain localhost sue2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by tszanon on 2007-09-14
Everything seems fine, as expected. Is the internet connection working fine?
Also, please post the output of these 2 commands. Let's see where it goes when:
```
ping nz.archive.ubuntu.com
telnet nz.archive.ubuntu.com 80

```
I'm expecting results like this:
```
$ ping nz.archive.ubuntu.com
PING ubuntu.citylink.co.nz (202.7.6.10) 56(84) bytes of data.
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=1 ttl=51 time=314 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=2 ttl=51 time=363 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=3 ttl=50 time=316 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=4 ttl=50 time=308 ms
--- ubuntu.citylink.co.nz ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3013ms
rtt min/avg/max/mdev = 308.837/325.817/363.657/22.032 ms

$ telnet nz.archive.ubuntu.com 80
Trying 202.7.6.10...
Connected to ubuntu.citylink.co.nz.
Escape character is '^]'.
^]

telnet> quit
Connection closed.
```

---

### Post by KiwiDalang on 2007-09-14
sue@sue2:~$ ping nz.archive.ubuntu.com
Took me a while to figure out ctrl-c to stop ping, but seems to be working ok I think

PING ubuntu.citylink.co.nz (202.7.6.10) 56(84) bytes of data.
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=1 ttl=53 time=241 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=2 ttl=53 time=248 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=3 ttl=53 time=246 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=4 ttl=53 time=248 ms
64 bytes from embassy.citylink.co.nz (202.7.6.10): icmp_seq=5 ttl=53 time=245 ms

--- ubuntu.citylink.co.nz ping statistics ---
6 packets transmitted, 5 received, 16% packet loss, time 5000ms
rtt min/avg/max/mdev = 241.404/245.912/248.727/2.592 ms
sue@sue2:~$ telnet nz.archive.ubuntu.com 80
Trying 202.7.6.10...
Connected to ubuntu.citylink.co.nz.
Escape character is '^]'.
^]

telnet> quit
Connection closed.

---

### Post by tszanon on 2007-09-14
> **KiwiDalang said:**
> sue@sue2:~$ ping nz.archive.ubuntu.com
Took me a while to figure out ctrl-c to stop ping, but seems to be working ok I think

Oh, my bad. I'm sorry. #-o
Everything seems ok. You computer can reach nz.archive.ubuntu.com. So, I think the problem is only in Synaptic. Let's review your sources. Please open /etc/apt/sources.list and paste it here. Press Alt+F2 and type:
```
gedit /etc/apt/sources.list
```

---

### Post by KiwiDalang on 2007-09-14
Just in case this was it, I grabbed the one off my other machine. Still get the same sort of result though:

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070415)]/ feisty main restricted
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release amd64 (20061025)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe main restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe main multiverse restricted
deb [http://www.e-oss.net/debian](http://www.e-oss.net/debian) ./
 

gives 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.6-2ubuntu3~feisty1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.6-2ubuntu3~feisty1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

etc

Maybe Synaptic is broken?

---

### Post by tszanon on 2007-09-15
> **KiwiDalang said:**
> 
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.6-2ubuntu3~feisty1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.6-2ubuntu3~feisty1_amd64.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

etc

Maybe Synaptic is broken?
Based on what you told me before, if you click on the above link, the file is downloaded as expected, right?

Anyway, Synaptic is just a front-end for apt-get. So, if something is broken, I would blame apt-get. What happens when you type
```
apt-get update
```
It's used to update the package list from the repositories you have in /etc/apt/sources.list. It should download the files without any error. Then, what happens when you type
```
apt-get upgrade
```
It should download all upgrades available for the packages you have installed and, if necessary, install also the dependancies. Here is where that error message should appear, if that package you're trying to download is an update, not a new installation.

I'm running out of ideas. We checked your internet connection, and it's ok. We checked your sources, and they're ok. Now, as you suggested, we're checking if Synaptic has any problems. As I stated above, I think the error message will come up again, showing that the problem isn't Synaptic either. Could it be low disk space? I don't think so, but what's the output of
```
df -l
```
Notice it's a lowercase L, not the number 1.

---

### Post by KiwiDalang on 2007-09-15
You're right; apt-get update produced the same errors.

I think that there is plenty of disk space. I haven't loaded too many toys onto this machine.

sue@sue2:~$ df -l
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             75545376   5042128  66665724   8% /
varrun                  239256       100    239156   1% /var/run
varlock                 239256         0    239256   0% /var/lock
procbususb              239256       104    239152   1% /proc/bus/usb
udev                    239256       104    239152   1% /dev
devshm                  239256         0    239256   0% /dev/shm
lrm                     239256     38972    200284  17% /lib/modules/2.6.20-16-generic/volatile

---

### Post by KiwiDalang on 2007-09-15
I have found the answer:

[http://ubuntuforums.org/archive/index.php/t-229834.html](http://ubuntuforums.org/archive/index.php/t-229834.html)
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg26767.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg26767.html)

I am using anon-proxy, via JAP/JonDo. It will not update when this is not running. Rather than remove anon-proxy at this point, I fired up JAP/JonDo, and set anonymity off (so it doesn't update through the proxy servers). That is working.

Thanks very much to Tszanon for setting me in the right direction in the hunt, and for teaching me some stuff in the process.

---

### Post by tszanon on 2007-09-16
> **KiwiDalang said:**
> I have found the answer:

[http://ubuntuforums.org/archive/index.php/t-229834.html](http://ubuntuforums.org/archive/index.php/t-229834.html)
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg26767.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg26767.html)

I am using anon-proxy, via JAP/JonDo. It will not update when this is not running. Rather than remove anon-proxy at this point, I fired up JAP/JonDo, and set anonymity off (so it doesn't update through the proxy servers). That is working.

Thanks very much to Tszanon for setting me in the right direction in the hunt, and for teaching me some stuff in the process.
Thanks! I'm sure I would never find that out. We both learned some things in the process.
I'm glad to know everything is fine now. :)

---


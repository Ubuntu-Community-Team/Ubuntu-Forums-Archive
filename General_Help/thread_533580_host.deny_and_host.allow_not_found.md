---
title: "host.deny and host.allow not found"
date: 2007-08-24
forum: General Help
---

### Post by satimis on 2007-08-24
Hi folks,


Ubuntu 7.04 lamp server amd64


The files host.deny and host.allow can't be found.

$ sudo find / -name hosts.deny
$ sudo find / -name hosts.allow
both w/o printout

$ sudo iptables -L```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination        

```

How to create them?  TIA


Edit:

I found following guide;
[http://ubuntuforums.org/showthread.php?t=450853](http://ubuntuforums.org/showthread.php?t=450853)

I'll create host.deny and host.allow according to its steps.

Further suggestion/advice would be appreciated.



B.R.
satimis

---

### Post by callan79 on 2007-08-24
> **satimis said:**
> 
$ sudo find / -name hosts.deny
$ sudo find / -name hosts.allow


Hi There,

I'm not running a server, but I use hosts.deny to ensure that only I have remote access to my SSH server.

Anyway the files are not there, in terminal you can do this :

```

cd /etc
sudo touch hosts.deny

```

Else if you want to create them AND add some stuff at the same time, then :

```

cd /etc
sudo nano hosts.deny

```

Once nano starts, fill your file up with the lines you need, then CTRL+O to save it, and CTRL+X to exit.

Cheers
Callan

---

### Post by satimis on 2007-08-24
> **callan79 said:**
> Hi There,

I'm not running a server, but I use hosts.deny to ensure that only I have remote access to my SSH server.

Anyway the files are not there, in terminal you can do this :

```

cd /etc
sudo touch hosts.deny

```

Else if you want to create them AND add some stuff at the same time, then :

```

cd /etc
sudo nano hosts.deny

```

Once nano starts, fill your file up with the lines you need, then CTRL+O to save it, and CTRL+X to exit.
Callan
Hi Callan,

Tks for your advice.

I have these 2 files created already.  They are only empty files.  Goole brought me many examples.  Can you give me some hints.  TIA

B.R.
satimis

---


---
title: "Open SSH Server:  E invalid operation openssh-server"
date: 2017-04-14
forum: General Help
---

### Post by AUDIOTEK on 2017-04-14
Never had that issue before.   I'm trying to install OpenSSH Server on Ubuntu 16.04 desktop and I'm getting that error

E invalid operation openssh-server


I did  sudo-apt update/upgrade

and still the same error

And can't find it in the Ubuntu Software Center

How can I get around this?

---

### Post by TheFu on 2017-04-14
**sudo apt install openssh-server**
What is the result?

---

### Post by AUDIOTEK on 2017-04-14
Here's the result I get    E invalid operation openssh-server

I managed to get it installed with   sudo apt-get install ssh   But I think that's the client       The machine I installed openssh will act as a server and I need to access it remotely from various computers.  Do I need put the authorized keys on the server?   Probably will be like 5 or 6 keys and sometimes I will access it with work computers.

---

### Post by Morbius1 on 2017-04-14
Nope, the "ssh" package contains both:
> apt show ssh | grep Depends

WARNING: apt does not have a stable CLI interface yet. Use with caution in scripts.

Depends: openssh-client (>= 1:6.6p1-2ubuntu2.8), openssh-server (>= 1:6.6p1-2ubuntu2.8)

---

### Post by steeldriver on 2017-04-14
```

E: Invalid operation openssh-server

```

suggests you missed the word [FONT=courier new]**install**[/FONT]

e.g.
```

$ sudo apt-get openssh-server
E: Invalid operation openssh-server

```

should be

```

$ sudo apt-get [COLOR=#0000ff]install[/COLOR] openssh-server

```

---

### Post by TheFu on 2017-04-14
Yes, that was my point. Sorry for being obtuse.
Showing the command AND the results sure does make a difference.

---

### Post by AUDIOTEK on 2017-04-14
It says already installed so I guess ```
[COLOR=#000000]sudo apt-get install ssh
``` worked   I went back in my bash history and the original error came from this [/COLOR]```
[COLOR=#000000]sudo apt-get install ssh-server
``` [/COLOR]

---

### Post by TheFu on 2017-04-14
ssh-server isn't a valid package.  That was the error.  I see this:
```
$ sudo apt-get install ssh-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ssh-server is a virtual package provided by:
  openssh-server:i386 1:7.2p2-4ubuntu2.1
  openssh-server 1:7.2p2-4ubuntu2.1
  dropbear-bin:i386 2016.72-1
  lsh-server 2.1-8
  dropbear-bin 2016.72-1
You should explicitly select one to install.

E: Package 'ssh-server' has no installation candidate
``` That is not the error reported above.

"Software Center" is the grandma interface into the package manager. I've never seen it or used it. Sorry.

---


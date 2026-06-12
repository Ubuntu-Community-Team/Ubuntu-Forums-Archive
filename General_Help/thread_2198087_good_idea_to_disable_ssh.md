---
title: "good idea to disable ssh?"
date: 2014-01-06
forum: General Help
---

### Post by timjonesthesecond on 2014-01-06
i read an article which states that
> 
  Because there are so many measures one can take reading for those sites is a good place to start. I can resume some of the basic measures:
[LIST=1]
[*]Change SSH port or disable (if you don't need it)
[/LIST]


i'm running a fresh install of ubuntu (desktop not server) and i dont think i will use ssh. so would it be a good idea to disable it? if so, how do i do so? thank you

---

### Post by tgalati4 on 2014-01-06
The ssh framework is used by a lot of processes that need encryption.  So it is not a good idea to remove it.

Open a terminal:

```
apropos ssh
```

Of course you can remove it and tell us what breaks.

---

### Post by Dave_L on 2014-01-06
It's mainly the SSH server, which handles incoming connections, that's the risk.

Check whether you have the package "openssh-server" installed.

You can check that with a package manager such as synaptic, or from the command line:
```
 dpkg-query --status openssh-server|grep Status:
```

If it's installed, then uninstall it if you don't need it. If you do need it, here's some information on configuring it to make it more secure:

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[http://www.thegeekstuff.com/2011/05/openssh-options/](http://www.thegeekstuff.com/2011/05/openssh-options/)

---

### Post by tgalati4 on 2014-01-07
The server is typically not installed by default, so it is normally not a risk, but if the OP wants to remove other ssh parts,  that could result in breakage.

```
apt-cache policy openssh-server
```

It might look like:

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache policy openssh-server
openssh-server:
  Installed: (none)
  Candidate: 1:6.0p1-3ubuntu1
  Version table:
     1:6.0p1-3ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages

---

### Post by deadflowr on 2014-01-07
> **timjonesthesecond said:**
> i read an article which states that


i'm running a fresh install of ubuntu (desktop not server) and i dont think i will use ssh. so would it be a good idea to disable it? if so, how do i do so? thank you

If you want to disable it, go right ahead.
But truth be told, as posted before, you can't turn something off if it was never actually installed.:P

The best way though, would be to remove the openssh-server package if you did have it installed.
You would have had to install it to begin with, so...

---

### Post by mastablasta on 2014-01-07
or make it more secure, use keys etc.... and then use it. it is an interesting experience when you control your home compuiter while being hunders of km away from home :-)

---


---
title: "Help! I cant open software center or download updates!"
date: 2015-08-26
forum: General Help
---

### Post by brennan3 on 2015-08-26
I don't know what i did but since the other day its not letting me open software center or download updates :( Thanks for your help! Will be replying ASAP.

---

### Post by v3.xx on 2015-08-26
Open a terminal

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

and enter

```
sudo apt-get update
```

and post the output using code tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by brennan3 on 2015-08-26
E: Syntax error /etc/apt/apt.conf.d/70debconf:3: Extra junk after value this is what i get.

---

### Post by oldos2er on 2015-08-26
It would help to see the entire output, and could you also post the output of ```
cat /etc/apt/apt.conf.d/70debconf
```

---

### Post by brennan3 on 2015-08-26
i think it maybe because i was trying to fix my internet problems by making the cache bigger since my friend did it and it worked heres the log
```

carousue@BrennansPC:~$ cat /etc/apt/apt.conf.d/70debconf
APT::Cache-Limit "100000000 // Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg: re-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
```

---

### Post by Yellow Pasque on 2015-08-26
^That's extremely hard to read, but it looks like you may have missed an " character after 10000000

---


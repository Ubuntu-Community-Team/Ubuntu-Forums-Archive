---
title: "pure-ftpd run from command line doesn't bind to port"
date: 2008-02-09
forum: General Help
---

### Post by whit on 2008-02-09
After years of happily running pure-ftpd on Gentoo, I'm trying to move an
operation over to Ubuntu. The default invocation does not work for us, since
we need to have several instances on the server running on different IPs.
The desire is to run it on Ubuntu with the same command line switches that
we've been using forever on the Gentoo box.

The problem I'm running into is that although it starts without complaint,
it doesn't actually bind to the port on the assigned IP. The process is
there to be seen with "ps",* but there's no port binding to be seen with
"netstat -na". Nor can it be connected to. This is true running 1.0.21 from
Ubuntu. It's true running 1.0.22 compiled from source.

Now, the default Ubuntu configuration (binding to all ports &c.) runs fine.
So there's got to be something I'm not familiar with in the Debian/Ubuntu
world that's causing this strange (to me) failure.

Thanks for any pointers on this.

Whit

PS: Why switch from Gentoo? The Gentoo project's just gotten too
uncoordinated, with too many gotchas in what should be simple program
upgrades. Ubuntu is sure immature around the edges, but looks to have more
future.

**Update:** But what's seen with ps is the command line that invoked it, switches and all, not the "pure-ftpd (SERVER)" process which would be shown if it were running correctly.

---

### Post by Ghuloomo on 2008-02-09
I don't have an idea what you're talking about :p ..

---

### Post by whit on 2008-02-09
I'm talking about the pure-ftpd ftp daemon, which can be run from a labrynth of configuration files through pure-ftpd-wrapper - the default in Ubuntu's install of it. However, if you have a server with many IPs, and you want to have several different pure-ftpd instances running on individual IPs among them, the way to invoke them isn't through pure-ftpd-wrapper, but directly on the command line. It's a standard way to start pure-ftpd, which works fine on Gentoo, but for some reason has a problem actually binding to the IP and port assigned when started this way in Ubuntu. Any clearer?

---

### Post by whit on 2008-02-10
Should I be looking at apparmor - a component of the default Ubuntu Server that I'm not familiar with? Would it be blocking the full invocation of a program from bash while allowing it to run normally from its init.d script?

Note: No profiles loaded in the default install:

```

# apparmor_status
apparmor module is loaded.
0 profiles are loaded.
0 profiles are in enforce mode.
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

```

Now I've removed apparmor according to [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor) and still pure-ftpd will not start from the command line. So what else could be blocking it from binding to the port just if it's started this way, and not from the overly-limited, capability-limiting pure-ftpd-wrapper script?

---


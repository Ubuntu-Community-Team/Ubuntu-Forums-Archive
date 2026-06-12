---
title: "Can't use Aptitude after termination during mid-install"
date: 2012-11-02
forum: General Help
---

### Post by golfromeo on 2012-11-02
Long story short, I was installing something via "sudo apt-get" and accidentally closed the terminal window that was doing it.

Now, apt-get install doesn't work, and apparently it's some issue to do with "libc6", as I get the following end-of-output after trying to install something:

```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I get the following output when trying to run "sudo apt-get install -f":

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 216122 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for any help you guys can give me, I really appreciate it.

---

### Post by ibjsb4 on 2012-11-02
Seems to be more than one way to fix this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Fcache%2Fdebconf%2Fconfig.dat+is+locked+by+another+process&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=var%2Fcache%2Fdebconf%2Fconfig.dat+is+locked+by+another+process&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by gerowen on 2012-11-02
Retry the command with the -f in the correct location as specified in the output you were given:

```

sudo apt-get -f install

```

If that doesn't work, try a reboot, if the problem persists, refer to this bug report:

[https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349469)

Looks like they're saying to run the following:
```

sudo fuser /var/cache/debconf/config.dat

```

Then kill each process listed.

---

### Post by golfromeo on 2012-11-02
Thanks for the help,

 I just ran the "sudo fuser" command as specified, and there weren't any processes listed.

---

### Post by golfromeo on 2012-11-02
Thanks guys, just solved it!

I had to reboot the machine and *then* run "install -f".

---

### Post by gerowen on 2012-11-02
Glad you got it figured out, :-)

---

### Post by ibjsb4 on 2012-11-02
Don't forget  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


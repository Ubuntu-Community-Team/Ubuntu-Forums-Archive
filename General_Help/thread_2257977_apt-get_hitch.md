---
title: "apt-get hitch"
date: 2014-12-23
forum: General Help
---

### Post by Pedroski55 on 2014-12-23
I keep getting this, what should I do?

Fetched 1,455 kB in 47s (30.6 kB/s)                                            
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.


pedro@pedro-bedro2:~$ sudo apt-get check
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.

---

### Post by Bashing-om on 2014-12-23
Pedroski55; Hello ;

That indicates a corrupted control file ... and maybe others also.

Let's remove the control file(s):
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial

```
and now rebuild these control files and resync the indexes :
```

sudo apt-get update

```

and make sure the package manager is in a happy state:
```

sudo apt-get upgrade

```

[INDENT][INDENT]I do expect
[INDENT][INDENT][INDENT][INDENT]all is finer than a frog's hair
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Pedroski55 on 2014-12-23
That did the trick! Thanks a lot, and Merry Christmas!

---

### Post by Bashing-om on 2014-12-23
Pedroski55; Great !

Pleased it worked out .
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---


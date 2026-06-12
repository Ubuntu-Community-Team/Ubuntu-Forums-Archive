---
title: "java and mysql packages"
date: 2016-05-02
forum: General Help
---

### Post by satimis on 2016-05-02
Hi all,

I'm going to install OpenIAM on Ubuntu 14.04.  

It requires;
JAVA		JDK 1.7
Database	        MySQL 5.6+

Please advise which packages shall I install on repo?  Thanks

Regards
satimis

---

### Post by ian-weisser on 2016-05-02
These are the versions of OpenJDK  in each release of Ubuntu. Note that -7 was dropped after 15.10.
```
$ rmadison openjdk-7-jdk
 openjdk-7-jdk | 7~u3-2.1.1~pre1-1ubuntu2    | precise/universe          | amd64, armel, armhf, i386, powerpc
 openjdk-7-jdk | 7u51-2.4.6-1ubuntu4         | trusty                    | amd64, arm64, armhf, i386, powerpc, ppc64el
 openjdk-7-jdk | 7u85-2.6.1-5                | wily                      | amd64, arm64, armhf, i386, powerpc, ppc64el

$ rmadison openjdk-8-jdk
 openjdk-8-jdk | 8u66-b01-5        | wily/universe          | amd64, arm64, armhf, i386, powerpc, ppc64el
 openjdk-8-jdk | 8u77-b03-3ubuntu3 | xenial                 | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 openjdk-8-jdk | 8u91-b14-2ubuntu1 | yakkety                | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x

$ rmadison openjdk-9-jdk
 openjdk-9-jdk | 9~b114-0ubuntu1 | xenial/universe  | amd64, i386
 openjdk-9-jdk | 9~b116-1ubuntu1 | yakkety/universe | amd64, i386

```


These are the versions of MySQL in each release of Ubuntu.
```
$ rmadison mysql-server
 mysql-server | 5.5.22-0ubuntu1         | precise          | all
 mysql-server | 5.5.35+dfsg-1ubuntu1    | trusty           | all
 mysql-server | 5.6.25-0ubuntu1         | wily             | all
 mysql-server | 5.7.11-0ubuntu6         | xenial           | all
 mysql-server | 5.7.12-0ubuntu2         | yakkety          | all

```

If you really want to use 1.7 and 5.6, you can't get there with supported packages from 14.04.
Wily (15.10) has supported packages of both, but will EOL in July.
You can use older packages, but they are not supported.
You can also learn to install manually.
Or you can use the stock versions in 14.04, 16.04 etc. Is MySql 5.5.35 really so bad?

---

### Post by satimis on 2016-05-02
Hi ian-weisser,

Thanks for your advice.

For installing and running OpenIAM following OS and packages are required;
```

OS		Ubuntu 14.04+
JAVA		JDK 1.7
Database	MySQL 5.6+
	
Application Server	JBoss 7.x (Included as part of the distribution)
Supported Browsers	Firefox (v40 and later)

```
I can install Ubuntu 16.04 - OS which is LTS

Are;
```

JAVA		JDK 1.7
Database	MySQL 5.6+

```
there, i.e. MySQL 5.7/5.8 etc?

Regards
satimis

---

### Post by ian-weisser on 2016-05-03
Already answered in Post #2.
No LTS release has supported versions of both. One regular release has supported versions of both.

The OpenIAM choice of dependency versions requirements, mixing old and new, causes the difficulty.

---


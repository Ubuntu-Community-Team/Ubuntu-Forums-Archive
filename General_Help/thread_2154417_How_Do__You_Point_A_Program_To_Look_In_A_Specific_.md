---
title: "How Do  You Point A Program To Look In A Specific Directory For Another Program When"
date: 2013-06-14
forum: General Help
---

### Post by FMFCorpsman on 2013-06-14
I downloaded JDK7U21 from Java and surprised myself and installed it with no problems from the terminal. I also downloaded Vuze which needs Java and looks for it when installing. Vuze readme.txt says to use a JAVA_PROGRAM_DIR option in the script, so I did and this iswhat I got, which is the same as I initially got when I tried installing Vuze the first time:

kl7jef@Patriot-1:~/Downloads/vuze$ ./azureus JAVA_PROGRAM_DIR="/home/jdk1.7.0_21/bin"
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
ls: cannot access /usr/lib/jvm: No such file or directory
Re-checking with GCJ (Sun Java recommended)..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm: No such file or directory
OOPS, unable to locate java exec in  /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://java.sun.com](http://java.sun.com)

As you can see I put Java in "/home/jdk1.7.0_21/bin"

Am I on the right track?

Any help is appreciated.  Thanks!

---

### Post by Bucky Ball on 2013-06-14
*Thread moved to **General Help**.*

No, I'm not following you around. ***Installation & Upgrades*** is, from the description of that sub-forum:

> For questions about upgrading and installation of your new Ubuntu OS.

 ;)

---

### Post by FMFCorpsman on 2013-06-14
And there I go again assuming Installation in the general sense lol!

---

### Post by steeldriver on 2013-06-14
```
./progname VAR=value
```

runs progname and **then **sets the value of VAR; what you want to do probably is the other way around i.e.

```
VAR=value ./progname
```

Alternatively, you could **export **VAR with its new value

```
export VAR=value
```

then

```
./progname
```

---

### Post by FMFCorpsman on 2013-06-14
I might be over my head, but I'm trying lol! I understand the use of ./ to execute file in current directory. I don't understand VAR. When I try and look it up, I keep getting sent to the enviromental variable Path=. What about using Path= and add it in the .bashrc? I tried, but it wouldn't let me type, so it was a no go. if you could explain a little more what the VAR represents and how and where it would be used, i would prefer that over messing with the .bashrc at my days old skill level!

---

### Post by HiImTye on 2013-06-14
PATH has to be all uppercase, as most other system variables
notice the difference between
```
echo $path
echo $Path
echo $PATH
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by steeldriver on 2013-06-14
sorry I just used VAR to mean a generic environment variable - in your case that would be

```
JAVA_PROGRAM_DIR="/home/jdk1.7.0_21/bin" ./azureus
```

or

```

export JAVA_PROGRAM_DIR="/home/jdk1.7.0_21/bin" 

./azureus

```

---

### Post by FMFCorpsman on 2013-06-15
Thank you Sir.

---


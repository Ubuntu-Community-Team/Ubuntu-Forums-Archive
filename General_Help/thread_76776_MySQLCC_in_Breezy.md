---
title: "MySQLCC in Breezy?"
date: 2005-10-15
forum: General Help
---

### Post by veraction on 2005-10-15
Just wondering, why isn't this in repositories/apt-get/synaptic for breezy?

[edit] nvm, I see there is something called MySQL Administrator under Applications -> Add Applications, so MySQLCC may be outdated?

---

### Post by DJ_Max on 2005-10-15
Yeah, it doesn't look like it's in the repo's anymore.

---

### Post by m0ns00n on 2005-10-20
Mysql-Admin and Mysql-Querybrowser together make you able to slowly and awkwardly do what you could do in mysqlcc in a wiffy. So it's again a *ding* on the head to the Ubuntu developers to get their act together and make responsible desicions about the software they package in the repositories. MysqlCC has been a must for me for a long while, as I work with MySQL every day at the office. After upgrading to breezy, loosing mysqlcc in the process, things take MUCH more time when mysql is concerned...

If you developers please would add mysqlcc again, I'd be a happy man!

---

### Post by justmehere on 2005-10-20
I need mySQLcc too as I'm connecting to a server with an older version of MySQL that the newer apps say is not supported.

---

### Post by ManLord on 2005-10-20
I also wondered where mysqlc took off.. hmm and packages like w32codecs are...??

---

### Post by alvonsius on 2005-10-21
Mee too ... please oh developers, bring back mysqlcc coz we need it ...

---

### Post by alvonsius on 2005-10-21
By the way, i found mysql deb in [http://packages.ubuntu.com/hoary/misc/mysqlcc](http://packages.ubuntu.com/hoary/misc/mysqlcc) i'm gonna try to install it and see if this thing work or not

EDIT:
It doesnt work, the error was

dpkg: dependency problems prevent configuration of mysqlcc:
 mysqlcc depends on libqt3c102-mt (>= 3:3.2.3-3); however:
  Package libqt3c102-mt is not installed.

I dont know where to find and honestly i'm afraid to install from deb (somebody please explain what is this lib for, and is there ok to install it straight from hoary's deb files). Hope the developer give mysqlcc another try in the repo ...

---

### Post by BIGtrouble77 on 2005-10-21
I had to install mysqlcc independently in hoary(didn't even know it was in the repos).  I haven't tried getting it running in breezy yet.  From what I remember, it wasn't that hard to install.  Just because it's not in the repositories doesn't mean you can't use it.

EDIT: This is turning out to be more of a pain than I thought.  Conflicting libraries... I tried installing libqt3c102-mt.deb from hoary and it won't work, it conflicts with breezy's libqt3-mt.  I got the Linux (x86, glibc 2.3) version of mysqlcc to work from mysql's site, but the fonts didn't work at all.  I couldn't get the mysqlcc Linux (x86, glibc 2.2) version to run at all.  I also tried compiling the source but had library issues.

So the glibc2.3 version works, but no fonts.  Anyone have any ideas to fix that?

---

### Post by eerik on 2005-10-22
I got mysqlcc work under ubuntu 5.10 (breezy) by compiling it from the source code.

Steps of my installation were:

1. downloaded the source code of the mysqlcc from [http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.2-src.tar.gz](http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.2-src.tar.gz)

2. compiled the source according to instructions from [http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/products/mysqlcc/install.html#build](http://sunsite.mff.cuni.cz/MIRRORS/ftp.mysql.com/products/mysqlcc/install.html#build) (see section 'Compiling MySQL Control Center under Linux/Unix')

Had, however, to overcome few problems before './configure' and 'make' worked :
- used './configure --with-qt=/usr/share/qt3' instead of './configure' 
- to replace #include <qpopmenu.h> by #include <qpopupmenu.h> in 2 header files (make will show you problematic file names in its error messages).
- to replace 'mysql_shutdown(mysql)' by 'mysql_shutdown(mysql,SHUTDOWN_DEFAULT)' at line 446 of the source file ../mysqlcc-0.9.2-src/shared/src/CMySQL.cpp

3. moved the executable to /usr/bin by 'sudo mv mysqlcc /usr/bin'
4. run executable by command 'mysqlcc &'

Fonts of the source-compiled mysqlcc are very ugly, however (as ugly as fonts of my Skype on breezy). Does somebody know the solution for the ugly- font-problem?

---

### Post by ss_theone on 2005-10-25
Just use the binaries for MySQL CC 0.9.4 for glibc 2.3. Works fine straight out of the box!

Here's one place to find it:
[http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz](http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz)

---

### Post by BIGtrouble77 on 2005-10-26
[QUOTE=ss_theone]Just use the binaries for MySQL CC 0.9.4 for glibc 2.3. Works fine straight out of the box!

Here's one place to find it:
[http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz](http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz)[/QUOTE]
Interesting, this one works fine.  I wonder why the version on the mysql site had problems.  Thanks for the link.

---

### Post by alvonsius on 2005-10-31
Yup, the glib version works on my breezy too, with one complaint ... why can't I use the style listed on my KDE Appereance and Theme?? It only give me 6 options of default style ... 

PS: Have you all try TORA (tora.sourceforge.com)??? Seems nice, but too complex. Yow all the developer ... bring back our MySQLCC ... ho ho ho ...

---

### Post by gbouro on 2005-11-08
[quote=ss_theone]Just use the binaries for MySQL CC 0.9.4 for glibc 2.3. Works fine straight out of the box!

Here's one place to find it:
[http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz]("http://ftp.iasi.roedu.net/mirrors/ftp.mysql.com/MySQLCC/mysqlcc-0.9.4-linux-glibc23.tar.gz")[/quote] 

That was a lifesaver.  Thanks for the pointer.

---

### Post by zordon on 2005-12-08
can't find that from link above...damn! any help? missing mysqlcc a lot...

---

### Post by gbouro on 2005-12-08
[quote=zordon]can't find that from link above...damn! any help? missing mysqlcc a lot...[/quote]

Google is your friend:

[http://www.google.com/search?q=mysqlcc-0.9.4-linux-glibc23.tar.gz&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial](http://www.google.com/search?q=mysqlcc-0.9.4-linux-glibc23.tar.gz&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial)

---

### Post by vitorsouza on 2005-12-16
[QUOTE=alvonsius]By the way, i found mysql deb in [http://packages.ubuntu.com/hoary/misc/mysqlcc](http://packages.ubuntu.com/hoary/misc/mysqlcc) i'm gonna try to install it and see if this thing work or not

EDIT:
It doesnt work, the error was

dpkg: dependency problems prevent configuration of mysqlcc:
 mysqlcc depends on libqt3c102-mt (>= 3:3.2.3-3); however:
  Package libqt3c102-mt is not installed.

I dont know where to find and honestly i'm afraid to install from deb (somebody please explain what is this lib for, and is there ok to install it straight from hoary's deb files). Hope the developer give mysqlcc another try in the repo ...[/QUOTE]

I just got mysqlcc working here. I downloaded from this place:

[http://download.softagency.net/mysql/Downloads/sarge/mysql/mysqlcc/](http://download.softagency.net/mysql/Downloads/sarge/mysql/mysqlcc/)

Then I installed it with:

```
dpkg -i --force-depends mysqlcc_0.9.2-1_i386.deb
```

It probably worked because the dependency libqt3c102-mt, which is now called libqt3-mt, was already installed. So far it hasn't crashed or anything, but I'll update this if I run into any trouble.

I too think the new MySQL Admin tools are crap... MySQLCC rocks!

V&#237;tor Souza

UPDATE: OK, just got a SEGFAULT by trying to open the query tool (Ctrl+Q)... *sigh*

---

### Post by noximyre on 2005-12-23
Has anyone gotten this to work on AMD64 (or has encountered the follow errors)? Compiling the 0.9.2 source mentioned above requires a newer version of Qt3 than exists in the repositories:

```

checking "if Qt Version in /usr/lib/qt3 is >= 3.0.5"... no
Please upgrade your Qt library to version 3.0.5 or higher
If you do have the correct version of QT installed somewhere
other than /usr/lib/qt3, please specify it as --with-qt= argument

```

Where can a get a version higher than 3.0.5?

Running the 0.9.4 binary mentioned above complains:

```

./mysqlcc: error while loading shared libraries: libXxf86vm.so.1: cannot open shared object file: No such file or directory

```

Running **locate libXxf86vm** show that it appears in:

```

/usr/lib/libXxf86vm.so.1
/usr/lib/libXxf86vm.so.1.0.0

```

So I don't know where it's looking. Any help will be greatly appreciated!

---

### Post by leinchu on 2006-01-10
&#36825;&#37324;&#26377;&#20010;0.94beta&#30340;&#29256;&#26412;&#65292;&#26377;&#27491;&#24335;&#29256;&#30340;&#21527;&#65311;
0.94beta&#22312;&#21644;mysql 5&#36830;&#25509;&#26102;&#32769;&#26159;&#20250;&#35828;&#25214;&#19981;&#21040;&#34920;1([bud] &#38169;&#35823; 1146: Table 'Exchange.1' doesn't exist)
[http://80.50.248.77/vol/d3/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.4-win32.zip](http://80.50.248.77/vol/d3/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.4-win32.zip)
&#35841;&#26377;&#30340;&#35805;&#40635;&#28902;&#21457;&#32473;&#25105;&#19968;&#20221;&#65306;lein_urg@163.com [email]leinchu@hotmail.com[/email]

There is mysqlcc 0.94 beta,anyone has a 0.94 version in state?
If you has ,please give me a copy,contact [email]lein_urg@163.com[/email] [email]leinchu@hotmail.com[/email] ,Thanks!
you can download 0.94 beta from [http://80.50.248.77/vol/d3/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.4-win32.zip](http://80.50.248.77/vol/d3/ftp.mysql.com/Downloads/MySQLCC/mysqlcc-0.9.4-win32.zip),


:rolleyes: My english is bad ,sorry

---

### Post by chantra on 2006-02-03
hi there,

 good news, i've finallymade my first deb package :)
  I built up mysqlcc-0.9.4's .deb package on a breezy platform.

it's available from this url:[debuntu.org]("http://debuntu.org/2006/02/12/3-mysqlcc-094").

I've just registered the url, therefore it might take one or 2 days from now before it gets fully accessible.

Hope it will work fine for you :p

---

### Post by gbouro on 2006-02-04
[quote=chantra]hi there,

 good news, i've finallymade my first deb package :)
  I built up mysqlcc-0.9.4's .deb package on a breezy platform.

it's available from this url:[http://debuntu.org/?id=1]("http://debuntu.org/?id=1").

I've just registered the url, therefore it might take one or 2 days from now before it gets fully accessible.

Hope it will work fine for you :p[/quote] 
Thanks!  Installed great.

One thing that never worked for me with the statically linked version that I am using and the .deb that you made was expanding the user list. I cannot see any users in this version of mysqlcc. I can create new ones and they are activated but I cannot see/edit them... 

Not a show-stopper, obviously, just a nuissance.

---

### Post by chantra on 2006-02-04
hi,

  cool, if it woks fine :) .

  I gave a try to the user thingy and it works fine for me. Have you checked that there were no error in your manipulation (check out the error box in the lower part of the console).

---

### Post by gbouro on 2006-02-06
[QUOTE=chantra]hi,

  cool, if it woks fine :) .

  I gave a try to the user thingy and it works fine for me. Have you checked that there were no error in your manipulation (check out the error box in the lower part of the console).[/QUOTE]
Mea culpa...  I had a .mysqlcc left over from a previous life.  I deleted the configuration and everything works.

---

### Post by chantra on 2006-02-07
cool then :KS

---

### Post by h0mer on 2006-02-15
this was EXACTLY what i've been looking for for ages. Thank you! Straightforward... and works flawlessly.:D

---


---
title: "Apache2 php module crashes out of now where? Weird problem.."
date: 2007-03-01
forum: General Help
---

### Post by mikestefff on 2007-03-01
My Ubuntu VPS server is running apache2, php5, mysql, postfix, and some other things. I am using drupal as my CMS - and have had no problems at all until last night. Out of no where my webserver went down. After ssh'ing in I tried to reload apache2 and got this error:

apache2: could not open document config file /etc/apache2/mods-enabled/php5.conf
                                                                         [fail]

So i navigated to /etc/apache2/mods-available and saw this after [ls -l]
(.....)
-rw-r--r-- 1 root root   72 Sep 27 11:54 mime_magic.load
-rw-r--r-- 1 root root   66 May 11  2006 perl.conf
-rw-r--r-- 1 root root   60 May 11  2006 perl.load
?--------- ? ?    ?       ?            ? php5.conf
?--------- ? ?    ?       ?            ? php5.load

Why would this happen out of no where - and what does it mean exactly?

Should I just reinstall php5, or the apache php modules? Will that cause other things to crash or uninstall??

Thanks

---

### Post by mikestefff on 2007-03-01
OK now this is really not making any sense. I cannot remove or install anything php related. It just keeps throwing errors that everything depends on php5-common. So i tried to reinstall php5-common but it wont let me know, i tried to reinstall php5, and the modules and nothing is working.

```
# apt-get install php5-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5: Depends: libapache2-mod-php5 (>= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed or
                 php5-cgi (>= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed
  php5-cgi: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-cli: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-gd: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-ldap: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-mhash: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-odbc: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-recode: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-snmp: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-sybase: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-xmlrpc: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
  php5-xsl: Depends: php5-common (= 5.1.6-1ubuntu2.1) but 5.1.6-1ubuntu2.2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-----------------

# apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed
  php5: Depends: php5-common (>= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed
  php5-mysql: Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed
  php5-mysqli: Depends: php5-common (= 5.1.6-1ubuntu2.2) but 5.1.6-1ubuntu2.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


Whats goin on?

---

### Post by mikestefff on 2007-03-01
I tried replacing php5.conf and php5.load in the mods-available dir but they will not let them be replaced or deleted. It just saying No such file or directory

---

### Post by mikestefff on 2007-03-01
I tried running apt-get -f install to fix all of the php problems and got this:

dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/php5-cli_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-cgi_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-mhash_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-ldap_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-xsl_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-sybase_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-snmp_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-recode_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-xmlrpc_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-gd_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-odbc_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/libapache2-mod-php5_5.1.6-1ubuntu2.2_i386.deb
 /var/cache/apt/archives/php5-common_5.1.6-1ubuntu2.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mikestefff on 2007-03-01
It appears there are tons of file errors like the first one..

#:/usr/lib/php5/20051025# ls -l
total 230
?--------- ? ?    ?        ?            ? gd.so
-rw-r--r-- 1 root root 86328 Jan 19  2006 imap.so
?--------- ? ?    ?        ?            ? ldap.so
?--------- ? ?    ?        ?            ? mhash.so
-rw-r--r-- 1 root root 45232 Feb 21 05:24 mysql.so
-rw-r--r-- 1 root root 98744 Feb 21 05:24 mysqli.so
?--------- ? ?    ?        ?            ? odbc.so
?--------- ? ?    ?        ?            ? recode.so
?--------- ? ?    ?        ?            ? snmp.so
?--------- ? ?    ?        ?            ? sybase_ct.so
?--------- ? ?    ?        ?            ? xmlrpc.so
?--------- ? ?    ?        ?            ? xsl.so

---

### Post by mikestefff on 2007-03-01
no one knows anything?

could really use some help please..

thanks

---

### Post by Mr. C. on 2007-03-01
mikesteff,

You are thrashing, trying random installs/uninstalls, without noticing the larger problem.

What does:

?--------- ? ? ? ? ? gd.so

mean or indicate?

The ls program cannot determine if the file is a directory, it cannot determine its ownership/group, nor size, nor date.  All the apt-get's in the world are not going to fix this.

I would judge by this alone you have a corrupted filesystem.  This would explain why "out of nowhere" you started experiencing these problems.

Reboot in single user mode and check the root, and other filesystems before any more damage is caused.  And then, slow down and pay attention to each and every error, and realize cascading affects occur with errors.

---

### Post by mikestefff on 2007-03-01
it is on a VPS - i cannot reboot in any specific manner..why would these get corrupted out of no where?

and its its a filesystem problem - then why would only php files be effected

---

### Post by Mr. C. on 2007-03-02
Its difficult to know for sure what the problem is with only a few details, but we have clues.

Here's what we know:

1) A number of files that cannot be read by ls(1) correctly.  This means that the stat(2) system call used by ls(1) is failing for those files.  This will only occur this way if there are some serious problems.  I won't go into any more technical reasons about the mechanics of the linux/Unix OS and system calls.

2) You are seeing this problem after installing a bunch of software.  Why would the file system get corrupted "out of no where?"  Perhaps the file or file system that your VPS is contained within has corruption (due to some previous crash or other reason).  Your recent install just starts using those latter portions of the file system.  Perhaps the disk itself that contains the file system has bad sectors or blocks, or is ready to fail.  These type of errors can occur.  Only someone who can see the dmesg output or look at the SMART data for the disk can know for sure.

3) The installers are failing with return error codes and broken pipes.  This is indicating something unexpected and anomalous.  Programs fail this way, especially when hardware is failing.

If this is a hosted system, contact their support.  If this is your system, figure out why the VPS' file system / partition / disk is having trouble.

MrC

---


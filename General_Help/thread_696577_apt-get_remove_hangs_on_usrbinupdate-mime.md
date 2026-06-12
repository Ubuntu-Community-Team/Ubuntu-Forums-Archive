---
title: "apt-get remove hangs on /usr/bin/update-mime"
date: 2008-02-14
forum: General Help
---

### Post by redemption on 2008-02-14
Hello,

I recently did an apt-get install that required html2text
Now, apt-get hangs at this point and hogs CPU.

ps -aux
```
root      4042  0.6 10.8  16768 14272 pts/0    S+   11:30   0:02 apt-get autoremove
root      4050  0.0  4.1   6832  5504 pts/1    Ss+  11:30   0:00 /usr/bin/dpkg --status-fd 16 --force-depends --force-remove-essential --remove html2text
root      4051  0.0  0.8   2576  1104 pts/1    S+   11:30   0:00 /bin/sh /var/lib/dpkg/info/html2text.postrm remove
root      4053 91.8  1.4   3596  1852 pts/1    R+   11:30   5:06 /usr/bin/perl /usr/sbin/update-mime
```

I am not sure if this is a problem with dpkg or perl. Is there a way I can forcefully remove html2text with dpkg?

---

### Post by jan quark on 2008-02-14
you can list all installed packages

with 

```
dpkg --list
```

and remove with

for packages installed with synaptic

```
sudo apt-get remove --purge package
```

for downloaded packages
```

sudo dpkg -r package

```

---

### Post by redemption on 2008-02-14
The problem is that both purge and remove commands hang on:

```
Removing html2text ...

```

Also:

```
root@54321:~/# dpkg-reconfigure html2text
/usr/sbin/dpkg-reconfigure: html2text is broken or not fully installed

```


The ps -aux output shows what is running when it hangs. Is there any way I can manually remove html2text? It appears that html2text has only been partially installed

EDIT: Issue appears to be with perl, as Makefile.pl fails if I try to re-install html2text (or any other pl).
EDIT: apt-get fails here:

```
root@56843:~# dpkg --configure -a
root@56843:~# apt-get remove html2text
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  html2text
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 274kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing html2text (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 html2text
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---


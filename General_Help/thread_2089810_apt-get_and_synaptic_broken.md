---
title: "apt-get and synaptic broken"
date: 2012-11-30
forum: General Help
---

### Post by kruget on 2012-11-30
Somehow i installed a 32bit deb to 64bit Xubuntu using Ubuntu Software Center. Tho it failed, it breaks my apt-get. Now apt-get stuck, refused to do anything before the problem fixed.

I tried to fix broken package using Synaptic, resulting in this error:

> dpkg: error processing bandwidthd:i386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:Tried "apt-get -f install", result in other error:> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libpcap0.8:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpcap0.8:i386
The following packages will be REMOVED:
  bandwidthd:i386
The following NEW packages will be installed:
  libpcap0.8:i386
0 upgraded, 1 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0 B/117 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing bandwidthd:i386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)So i tried to reinstall as its requested, only to get another error:
sudo apt-get install bandwidthd:i386
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 bandwidthd:i386 : Depends: libpcap0.8:i386 (>= 0.9.8) but it is not going to be installed
                   Depends: ucf:i386 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
What should i do now?

- - - - - EDIT, Solved - - - - - -
sudo gedit /var/lib/dpkg/status

then remove all segment mentioned the culprit.

Solved.

---

### Post by LonghornCS13 on 2012-11-30
You need to try to manually remove the packages. Open a terminal and type:
```

cd /var/lib/dpkg/info
sudo rm bandwidthd:i386.*

```Then clean it up in  dpkg:

```

sudo dpkg --remove --force-remove bandwithd:i386

```I believe that should work...

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by kruget on 2012-11-30
> **LonghornCS13 said:**
> You need to try to manually remove the packages. Open a terminal and type:
```

cd /var/lib/dpkg/info
sudo rm bandwidthd:i386.*

```Then clean it up in  dpkg:

```

sudo dpkg --remove --force-remove bandwithd:i386

```I believe that should work...

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)
sudo dpkg --remove --force-remove bandwithd:i386 resulted in error:

dpkg: error: unknown force/refuse option `remove'

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by dino99 on 2012-11-30
sudo apt-get purge bandwidthd:i386

should work too.

note: you need the exact name (not bandwithd , with is false)

---

### Post by kruget on 2012-11-30
> **dino99 said:**
> sudo apt-get purge bandwidthd:i386

should work too.

note: you need the exact name (not bandwithd , with is false)

That still resulted in error:

> sudo apt-get purge bandwidthd:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bandwidthd:i386*
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 201 kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing bandwidthd:i386 (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

:(

---

### Post by Elfy on 2012-11-30
sudo dpkg --remove --force-remove bandwithd:i386

should be 

sudo dpkg --remove --force-remove-reinstreq bandwithd

I believe

---

### Post by LonghornCS13 on 2012-11-30
> **Elfy said:**
> sudo dpkg --remove --force-remove bandwithd:i386

should be 

sudo dpkg --remove --force-remove-reinstreq bandwithd

I believe


I think this is right. I was forgetting that reinstreq flag..

---

### Post by kruget on 2012-12-01
> **Elfy said:**
> 
sudo dpkg --remove --force-remove-reinstreq bandwithd


That give me this:

> dpkg: warning: there's no installed package matching bandwithd

But synaptic and apt-get still broken, and sudo apt-get install -f still give me this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libpcap0.8:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libpcap0.8:i386
The following packages will be REMOVED:
  bandwidthd:i386
The following NEW packages will be installed:
  libpcap0.8:i386
0 upgraded, 1 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0 B/117 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: error processing bandwidthd:i386 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any other suggestion?

---

### Post by BrandonIngalls on 2012-12-01
Shouldn't the command be
> sudo dpkg --remove --force-remove-reinstreq bandwithd:i386

---

### Post by kruget on 2012-12-02
it doesn't work. Fortunately i found a solution on [iasptk]("http://www.iasptk.com/ubuntu-fix-broken-package-best-solution") via [ptheo]("http://askubuntu.com/a/182872/85510"):

sudo gedit /var/lib/dpkg/status

then remove all segment mentioned the culprit.

Solved.

---


---
title: "Cannot Update"
date: 2023-02-19
forum: General Help
---

### Post by shane_faulkinbury2 on 2023-02-19
I installed OpenIffice last week and I was unaware the I could not have LibreOffice installed.  Now I am having a problem updating from SoftWare Update.  I was told that I had to completely remove LibreOffice to fix this.  Here is what I need to get rid of, but am unable too.

[Code 1:7.3.7-0ubuntu0.22.04.2 amd64 [installed,automatic]libreoffice-core/jammy-proposed,now 1:7.3.7-0ubuntu0.22.04.2 amd64 [installed,automatic]
libreoffice-math/jammy-proposed,now 1:7.3.7-0ubuntu0.22.04.2 amd64 [installed,automatic]
libreoffice-style-colibre/jammy-proposed,jammy-proposed,now 1:7.3.7-0ubuntu0.22.04.2 all [installed,auto-removable]
libreoffice-writer/jammy-proposed,now 1:7.3.7-0ubuntu0.22.04.2 amd64 [installed]
```


Here is what I get when I [code]rm
``` it and try to purge it.

```
sudo apt purge libreoffice-commonReading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudo apt purge libreoffice-math
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
                      Recommends: libreoffice-math but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudo apt purge libreoffice-core
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed or
                                  libreoffice-core-nogui (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
                    Depends: libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
                      Depends: libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
               Depends: libreoffice-core (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed or
                        libreoffice-core-nogui (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudo apt purge libreoffice-base-core
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-base-core (= 1:7.3.7-0ubuntu0.22.04.2) but it is not going to be installed
                      Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudo rm libreoffice-base-core
rm: cannot remove 'libreoffice-base-core': No such file or directory
root@none-OptiPlex-3020:/home/none# sudo rm libreoffice-core
rm: cannot remove 'libreoffice-core': No such file or directory
root@none-OptiPlex-3020:/home/none# sudo apt purge libreoffice-style-colibre
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

Can someone please tell me how to remove the packages?

---

### Post by MAFoElffen on 2023-02-20
Have you tried(?)
```

sudo apt remove --purge libreoffice* python3-uno

```

---

### Post by ActionParsnip on 2023-02-20
Disable the proposed repo. It isn't for casual users

---

### Post by civilpolisen on 2023-02-20
I got this same error earlier and I often get errors when updating Ubuntu. 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get autoremove
```

I very often get error message as similar to below:

```
The following packages have been kept back:  sosreport
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
The solution!
```
$ sudo apt list --upgradable

$sudo apt install sosreport --fix-broken


```

The solution!

List your failing installs and in the same window or in a new window go through them all and do the "install --fix-broken" manouver!
In this particular case, with the LibreOffice, I believe the first one will depend on the others and the install will fix all errors.
So... even if there are 17 errors, it happens, you need not to do 17 single installs!

It's all written on your screen.

---

### Post by shane_faulkinbury2 on 2023-02-21
I updated and upgraded and then got this -
```
sudo apt auto cleanE: Invalid operation auto
root@none-OptiPlex-3020:/home/none# sudo apt auto clean
E: Invalid operation auto
root@none-OptiPlex-3020:/home/none# sudo apt autoclean
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
root@none-OptiPlex-3020:/home/none# sudo apt autoremove
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@none-OptiPlex-3020:/home/none# sudp apt list --upgradable
Command 'sudp' not found, did you mean:
  command 'ssdp' from snap ssdp (0.0.1)
  command 'sup' from deb sup (20100519-3)
  command 'sudo' from deb sudo (1.9.9-1ubuntu2.2)
  command 'sudo' from deb sudo-ldap (1.9.9-1ubuntu2.2)
  command 'sfdp' from deb graphviz (2.42.2-6)
See 'snap info <snapname>' for additional versions.
root@none-OptiPlex-3020:/home/none# sudo apt install sosreport --fix-broken
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:7.3.7) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 python3-uno : Depends: libreoffice-common (>= 1:7.0.0~alpha~) but it is not going to be installed
 sosreport : Depends: python3-magic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

---

### Post by civilpolisen on 2023-02-21
```
root@none-OptiPlex-3020:/home/none# sudo apt install sosreport --fix-broken
```

Excuse me for bad writing! sosreport was my package at the time of writing! 

Look what packages are missing for you, in your case!

```

sudo apt install libreoffice-core --fix-broken
sudo apt install libreoffice-math --fix-broken
sudo apt install libreoffice-writer --fix-broken
sudo apt install python3-uno --fix-broken

```

Watch what happens, because when you install core the math and writer may also install at the same time!
I don't know, but these things happens from time to time, when installing things that depends on one another!

Other than that, you're doing good!

---

### Post by Impavidus on 2023-02-22
> **civilpolisen said:**
> I very often get error message as similar to below:

```
The following packages have been kept back:  sosreport
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```
There's no error message there. There's one package kept back, but that's not an error. It could be that the package is kept back for phased updates, or maybe because some dependency is unavailable (wich is a repository error and not fixable from your computer, unless you switch repositories or manage your own) or you pinned something or your repositories are wrongly configured. But nothing wrong as far as the package manager is concerned.

> **shane_faulkinbury2 said:**
> I updated and upgraded and then got this -
Have you also tried the suggestions in post #2 and 3?

BTW, no need for sudo when you already have a root shell.

> **civilpolisen said:**
> ```
root@none-OptiPlex-3020:/home/none# sudo apt install sosreport --fix-broken
```

Excuse me for bad writing! sosreport was my package at the time of writing! 

Look what packages are missing for you, in your case!

```

sudo apt install libreoffice-core --fix-broken
sudo apt install libreoffice-math --fix-broken
sudo apt install libreoffice-writer --fix-broken
sudo apt install python3-uno --fix-broken

```

Watch what happens, because when you install core the math and writer may also install at the same time!
I don't know, but these things happens from time to time, when installing things that depends on one another!

Other than that, you're doing good!
But OP wants to remove libreoffice, not install it.

Anyway, the manual says (man apt-get) that when you use --fix-broken with install/remove and a package name, it should be a full solution. Without any package on the command line, apt will try to figure it out automatically. If it doesn't do what you want, you can revert to the lower level tools:```
sudo dpkg --remove somepackage
```

---

### Post by shane_faulkinbury2 on 2023-02-22
Sorry, I had to work, got off and supper.  I just got online.  I ran a > **apt list --installed**/[QUOTE] and see [QUOTE]openoffice4.1.13-freedesktop-menus

So, I ran a > [COLOR=#000000][FONT=&quot]sudo dpkg --remove [/FONT][/COLOR]openoffice4.1.13-freedesktop-menus[COLOR=#000000][FONT=&quot]
 [/FONT][/COLOR]


I do a Software Update and still get

---

### Post by shane_faulkinbury2 on 2023-02-22
Sorry, I had to work, got off and supper.  I just got online.  I ran a > **apt list --installed**/[QUOTE] and see [QUOTE]openoffice4.1.13-freedesktop-menus

So, I ran a > [COLOR=#000000][FONT=&amp]sudo dpkg --remove [/FONT][/COLOR]openoffice4.1.13-freedesktop-menus[COLOR=#000000][FONT=&amp]
 [/FONT][/COLOR]


I do a Software Update and still get

---

### Post by shane_faulkinbury2 on 2023-03-01
I guess I'm going to have to reinstall my entire OS and purge Libreoffice before installing Openoffice?

---

### Post by monkeybrain20122 on 2023-03-01
It begs the question. Why do you want to install openoffice instead of Libreoffice? OO's development stalled years ago and LO is the active fork.

---

### Post by MAFoElffen on 2023-03-02
Just me. I tried to stay informed. 

OpenOffice started life as StarOffice by Sun Microsystems, which the name later changed to OpenOffice. For many years, OpenOffice was the choice of many Linux Distro's as their office suite. 

As many here know, Sun was bought by Oracle. As with many things that Oracle bought by that purchase, Oracle abandoned OpenOffice and let it die. OpenOffice, is a discontinued open-source office suite. That was 2011. They gave the code to Apache, which became Apache OpenOffice. 

In the meanwhile, their were already (mostly opensource) branches of that code that had active development- Libreoffice, Apache OpenOffice, Collabora Online and NeoOffice.

Brazil was a major push with active development of LibreOffice, as the Brazilian Government used that as their suite of applications. This is what probably, in my opinion, in reality, saved the project.

So +1 with asking why you want to go with an outdated application, when LibreOffice is clearly the front runner there?

---

### Post by Impavidus on 2023-03-02
A fresh install sounds like overkill.

Without the error messages coming from the command line tools like apt-get, we cannot tell you what to do. In posts #8 and 9, you haven't shown any output, other than that there are errors, without the contents of the error message.

---


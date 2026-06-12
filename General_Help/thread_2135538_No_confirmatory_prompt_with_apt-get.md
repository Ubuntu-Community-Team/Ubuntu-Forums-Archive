---
title: "No confirmatory prompt with apt-get"
date: 2013-04-14
forum: General Help
---

### Post by vasa1 on 2013-04-14
I seem to remember that *sudo apt-get install package_name* would prompt me to continue or not before actually starting a download but the last few times it hasn't! I've marked the place at which I think the prompt would appear. And the prompt would be a sort of "Do you want to continue Y/N" type of thing. 


```

[10:41 PM] ~/Desktop/temp $ sudo apt-get install perl-doc
[sudo] password for vasa1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  groff
The following NEW packages will be installed:
  perl-doc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,123 kB of archives.
After this operation, 13.2 MB of additional disk space will be used. ****************
Get:1 http://archive.ubuntu.com/ubuntu/ quantal-updates/main perl-doc all 5.14.2-13ubuntu0.2 [8,123 kB]
Fetched 8,123 kB in 3min 45s (36.1 kB/s)                                                                                                                               
Selecting previously unselected package perl-doc.
(Reading database ... 201664 files and directories currently installed.)
Unpacking perl-doc (from .../perl-doc_5.14.2-13ubuntu0.2_all.deb) ...
Adding 'diversion of /usr/bin/perldoc to /usr/bin/perldoc.stub by perl-doc'
Processing triggers for man-db ...
Setting up perl-doc (5.14.2-13ubuntu0.2) ...

```

I haven't set up any alias to not see the prompt:
```
       -y, --yes, --assume-yes
           Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such as changing a held package,
           trying to install a unauthenticated package or removing an essential package occurs then apt-get will abort. Configuration Item: APT::Get::Assume-Yes.

```

---

### Post by Vaphell on 2013-04-14
maybe it's because you install only one package that you explicitly gave as a parameter? What happens when you try to install something with a bunch of dependencies?

---

### Post by deadflowr on 2013-04-14
I usually get no confirmation when I'm only installing a single package, as you have here.
The confirmation happens when I entered my password.

If I install a package which has a few dependencies/extra packages it needs, or will also install, then I get a yes/no confirmation.

---

### Post by vasa1 on 2013-04-14
Okay, that's the answer. I just tried *sudo apt-get install konqueror* and saw this:
```
0 upgraded, 104 newly installed, 0 to remove and 0 not upgraded.
Need to get 68.2 MB of archives.
After this operation, 180 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```
And I confirmed it with *sudo apt-get install mousepad* which showed just the one package and installed without a prompt:
```
The following NEW packages will be installed:
  mousepad
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 101 kB of archives.
After this operation, 751 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ quantal/universe mousepad i386 0.2.16-6ubuntu1 [101 kB]
Fetched 101 kB in 2s (45.7 kB/s)   

```

---

### Post by vasa1 on 2013-04-15
```
sudo apt-get install -s package_name
``` would be useful to know what would be installed because -s does a simulation only.

---

### Post by OmgItsPixelated on 2013-04-15
> **vasa1 said:**
> ```
sudo apt-get install -s package_name
``` would be useful to know what would be installed because -s does a simulation only.

Oh, thanks for that. A neat trick to use next time I install some stuff from the terminal.

---


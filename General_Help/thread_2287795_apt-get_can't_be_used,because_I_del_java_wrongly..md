---
title: "apt-get can't be used,because I del java wrongly."
date: 2015-07-22
forum: General Help
---

### Post by andy140 on 2015-07-22
here is the output,I don't know how to deal with it,please help me thank you very much.

bd@ubuntu:~$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
vim is already the newest version.
The following packages will be REMOVED:
  jdk1.8.0-45
0 upgraded, 0 newly installed, 1 to remove and 210 not upgraded.
1 not fully installed or removed.
After this operation, 245 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 86292 files and directories currently installed.)
Removing jdk1.8.0-45 (1.8.045-1) ...
admindir /var/lib/alternatives invalid
admindir /var/lib/alternatives invalid
dpkg: error processing package jdk1.8.0-45 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 jdk1.8.0-45
E: Sub-process /usr/bin/dpkg returned an error code (1)
bd@ubuntu:~$

---

### Post by Vladlenin5000 on 2015-07-22
Hi and welcome.

You can try

```
sudo dpkg --purge --force-all jdk1.8.0-45
sudo apt-get install -f
```

---

### Post by andy140 on 2015-07-22
Thank you Vladlenin, I follow your advice,but it accurs some question in the following:
bd@ubuntu:~$ sudo dpkg --purge --force-all jdk1.8.0-45
(Reading database ... 86292 files and directories currently installed.)
Removing jdk1.8.0-45 (1.8.045-1) ...
admindir /var/lib/alternatives invalid
admindir /var/lib/alternatives invalid
dpkg: error processing package jdk1.8.0-45 (--purge):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 jdk1.8.0-45

---

### Post by Vladlenin5000 on 2015-07-22
A few suggestions [here]("http://askubuntu.com/questions/619889/i-have-problem-executing-apt-get").

---

### Post by Bucky Ball on 2015-07-22
Welcome. I suggest you try these commands, one after the other. Your machine needs to be updated/upgraded and that is not helping your issue.

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Report any and all errors. If there are none:

```
sudo apt-get install vim
```

Let us know what happens. Might also help if you let us know how you uninstalled jdk.

---

### Post by andy140 on 2015-07-22
> **Bucky Ball said:**
> Welcome. I suggest you try these commands, one after the other. Your machine needs to be updated/upgraded and that is not helping your issue.

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Report any and all errors. If there are none:

```
sudo apt-get install vim
```

Let us know what happens. Might also help if you let us know how you uninstalled jdk.

Hi,thank you for your answer,I have tried these command on after another.
But when I type these command,it occur some same problems,such as:
Preconfiguring packages ...
(Reading database ... 86292 files and directories currently installed.)
Removing jdk1.8.0-45 (1.8.045-1) ...
admindir /var/lib/alternatives invalid
admindir /var/lib/alternatives invalid
dpkg: error processing package jdk1.8.0-45 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 jdk1.8.0-45
E: Sub-process /usr/bin/dpkg returned an error code (1)
I don't know how to deal with it. When can't rember clearly about how to uninstall jdk,It is likey
that I del the install package and change the environment variables,such JAVA_HOME and PATH.

---

### Post by andy140 on 2015-07-22
> **Vladlenin5000 said:**
> A few suggestions [here]("http://askubuntu.com/questions/619889/i-have-problem-executing-apt-get").
Yeah!Thank you,I have Solved my problem:)
Here are the commands:
sudo rm -ri /usr/java/
sudo dpkg -r --force-all jdk1.8.0-45

and the final res:
bd@ubuntu:~$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree
Reading state information... Done
vim is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 210 not upgraded.
bd@ubuntu:~$
Thank everyone who help me~

---

### Post by Bucky Ball on 2015-07-22
Good news. Please mark thread as solved. See the first link in my signature. Good luck. :)

---


---
title: "apt-get can't be used. Ask for help!"
date: 2018-04-29
forum: General Help
---

### Post by peyogoat on 2018-04-29
Only update can be used, other command such as install, upgrade cannot be used.
The terminal display:


```
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libpam-systemd : Depends: systemd (= 229-4ubuntu21.2) but 229-4ubuntu21 is installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu21) but 229-4ubuntu21.2 is installed
```



 I am the Ubuntu image on AWS.It suddenly went wrong.I searched a lot of methods, but I still didn't solve them.I search for a solution in the search engine, usually by replacing the 229-4ubuntu21 version of systemd with 229-4ubuntu2. 2, but I can't replace it, and I can't delete systemd to reinstall it.A lot of the services of the system depend on systemd, how should I solve this problem?
I've been using the mirror's own apt source.Now that's the problem, I don't know how to fix it...
Ask for help!!

---

### Post by PaulW2U on 2018-04-29
The output that you have quoted is showing you the command that you need to run. Assuming that you are not logged in as the root user, try:
```
sudo apt-get -f install
```
Does that solve your problem?

---

### Post by peyogoat on 2018-04-29
> **PaulW2U said:**
> The output that you have quoted is showing you the command that you need to run. Assuming that you are not logged in as the root user, try:
```
sudo apt-get -f install
```
Does that solve your problem?

I also ran this command.

It does prompt me it was going to install systemd, but when it started the installation, it is prompted for a bunch of warnings, all about the missing of lib. And an error occured while covering /lib/systemd/systemd , it received the Broken pipe signal. Finally, the systemd 229-4ubuntu21.2 version cannot be installed successfully.

The terminal prompted this:
```

The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-ui systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 127 not upgraded.
4 not fully installed or removed.
Need to get 0 B/3,634 kB of archives.
After this operation, 16.4 kB of additional disk space will be used.
Do you want to continue? [Y/n]Y
dpkg: warning: files list file for package...
.....

dpkg: warning: files list file for package 'libmosquitto-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjpeg8:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjsoncpp1:amd64' missing; assuming package has no files currently installed
(Reading database ... 282898 files and directories currently installed.)
Preparing to unpack .../systemd_229-4ubuntu21.2_amd64.deb ...
Unpacking systemd (229-4ubuntu21.2) over (229-4ubuntu21) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_229-4ubuntu21.2_amd64.deb (--unpack):
 trying to overwrite '/lib/systemd/systemd', which is also in package systemd-sysv 229-4ubuntu21
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
addgroup: The group `systemd-journal' already exists as a system group. Exiting.
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for ureadahead (0.100.0-19) ...
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_229-4ubuntu21.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What should I do? Please help!

---

### Post by peyogoat on 2018-04-29
How can I let others know I have replied them?

---

### Post by peyogoat on 2018-05-07
I've solved the problem.This problem can be solved by using a  ```
dpkg
``` command to install the dependent software version on Lauchpad.In the process, you can use ```
-force-all
``` to ignore dependencies when deleting software.The commands used to resolve the process have been placed in this blog. The blog is written in Chinese, but the command should be understandable.
The blog:
&#20851;&#20110;&#35299;&#20915;Ubuntu&#19979;apt-get&#30340;Unmet dependencies&#20381;&#36182;&#38169;&#35823;:[https://blog.csdn.net/peyogoat/article/details/80229683](https://blog.csdn.net/peyogoat/article/details/80229683)

---


---
title: "Add-apt command not working with software-properties-common installed."
date: 2019-02-21
forum: General Help
---

### Post by rooster14250 on 2019-02-21
Hello. I am having problems adding repositories with add-apt. I already checked my software-properties-common installation, and the package is up to date. I am running 18.0.4 currently. Is there some config file that needs to be modified to enable this command? Thanks in advance.

---

### Post by #&amp;thj^% on 2019-02-21
Hello can you give this a try:
```
sudo apt install --reinstall software-properties-common python-software-properties
```
Also can you show us from the terminal any output from an attempted failure from "add-apt"

---

### Post by rooster14250 on 2019-02-21
I ran this command
(the python-software-properties package didn't work)
```

~$ sudo apt install --reinstall software-properties-common

```
and got 
```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/9,908 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 148833 files and directories currently installed.)
Preparing to unpack .../software-properties-common_0.96.24.32.7_all.deb ...
Unpacking software-properties-common (0.96.24.32.7) over (0.96.24.32.7) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for dbus (1.12.2-1ubuntu1) ...
Setting up software-properties-common (0.96.24.32.7) ...



```
When I tired add-apt again, I got another message about not finding the command. Thanks for the suggestion and speedy response though!

---

### Post by #&amp;thj^% on 2019-02-21
One more please:
```
sudo apt --fix-broken install python-pycurl python-apt
```
I need you to show us the command you are using to add the repos with.

---

### Post by rooster14250 on 2019-02-21
I was just about to upload the add-apt command that I was using when I realized that I made a mistake. I used ```
 add-apt repository multiverse
``` when I should have used ```
add-apt-repository multiverse
```  :oops: Oops. Oh well, live and learn. Thanks.

---


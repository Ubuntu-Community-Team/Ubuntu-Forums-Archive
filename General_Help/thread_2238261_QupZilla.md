---
title: "QupZilla"
date: 2014-08-06
forum: General Help
---

### Post by rickytikki on 2014-08-06
Hello ive recently been lookin and trying different web brosers to use and play with i recently came up on QupZilla looks good lightweight and i wanted to see what it has to offer. so i add the rep and update it and try to insstall it and im getting an error with some lib uses i dont really understand whats going on other than seing the errors i dont know how to go about fixing this issue perhaps u guys or gals can help.

```

$ sudo add-apt-repository ppa:nowrep/qupzilla -good zero errors
$ sudo apt-get update -good zero errors
$ sudo apt-get install qupzilla   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libqupzilla1
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  qupzilla
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,953 kB of archives.
After this operation, 15.1 MB of additional disk space will be used.
(Reading database ... 205780 files and directories currently installed.)
Preparing to unpack .../qupzilla_1.6.6-1~trusty_amd64.deb ...
Unpacking qupzilla (1.6.6-1~trusty) ...
dpkg: error processing archive /var/cache/apt/archives/qupzilla_1.6.6-1~trusty_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/qupzilla/libMouseGestures.so', which is also in package libqupzilla1 1.6.0-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/qupzilla_1.6.6-1~trusty_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
skynet@T1000:~$ 
``` 

could it be my mouse pointer that im using? or is it that the browser isnt 64bit? please help i really want to try this browser out.. thanx any suggestion is appreciated

---

### Post by claracc on 2014-08-07
Perhaps you first have to remove libqupzilla1 as it is addressed:

Open a xterm with ctrl+alt+T

and then run ```
sudo apt-get autoremove
```

Then, try again to install qupzilla from the ppa.

---

### Post by rickytikki on 2014-08-07
what i ended up doing was i added the repository intalled through  software center and upgraded through terminal i was trying to get the  latest version of qupzilla the version in software center is 1.6 or lower i  believe and i wanted latest stable release 1.6.6 

```

sudo add-apt-repository ppa:nowrep/qupzilla
sudo apt-get update

```
installed through software central 
```

sudo apt-get upgrade

```
Now i have 1.6.6 which is kewl :p

---


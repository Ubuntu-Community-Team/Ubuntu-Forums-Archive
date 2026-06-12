---
title: "Gimp Startrail plugin instilation"
date: 2021-11-07
forum: General Help
---

### Post by Joe_Linux on 2021-11-07
[https://www.facebook.com/astronomylinux/posts/who-needs-startrail-plugin-for-gimpopen-the-terminal-and-runsudo-apt-install-gim/2272501992854642/](https://www.facebook.com/astronomylinux/posts/who-needs-startrail-plugin-for-gimpopen-the-terminal-and-runsudo-apt-install-gim/2272501992854642/)
I found the above link to install startrail.py In Gimp 2.10.24 in Ubuntu 18.04. the post their is from (12/29/19). I tried it and received the following error
```
joe@joe-GA-78LMT-USB3:~$ sudo apt-get install gimp-python
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'gimp' instead of 'gimp-python'
The following additional packages will be installed:
  gimp-data libamd2 libbabl-0.1-0 libcamd2 libccolamd2 libcholmod3
  libgegl-0.3-0 libgimp2.0 libmetis5 libumfpack5 python-cairo python-gobject-2
  python-gtk2
Suggested packages:
  gimp-help-en | gimp-help gimp-data-extras python-gobject-2-dbg
  python-gtk2-doc
The following NEW packages will be installed:
  gimp gimp-data libamd2 libbabl-0.1-0 libcamd2 libccolamd2 libcholmod3
  libgegl-0.3-0 libgimp2.0 libmetis5 libumfpack5 python-cairo python-gobject-2
  python-gtk2
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.9 MB of archives.
After this operation, 76.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libgimp2.0 amd64 2.8.22-1 [765 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 gimp-data all 2.8.22-1 [7,800 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 python-cairo amd64 1.16.2-1 [56.4 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 python-gobject-2 amd64 2.28.6-12ubuntu3 [180 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 python-gtk2 amd64 2.24.0-5.1ubuntu2 [619 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libbabl-0.1-0 amd64 0.1.44-1 [249 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libamd2 amd64 1:5.1.2-2 [19.5 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libcamd2 amd64 1:5.1.2-2 [20.9 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libccolamd2 amd64 1:5.1.2-2 [21.7 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libmetis5 amd64 5.1.0.dfsg-5 [169 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libcholmod3 amd64 1:5.1.2-2 [300 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 libumfpack5 amd64 1:5.1.2-2 [229 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 libgegl-0.3-0 amd64 0.3.30-1ubuntu1 [827 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/universe amd64 gimp amd64 2.8.22-1 [3,672 kB]
Fetched 14.9 MB in 7s (2,038 kB/s)                                             
Selecting previously unselected package libgimp2.0.
(Reading database ... 335683 files and directories currently installed.)
Preparing to unpack .../00-libgimp2.0_2.8.22-1_amd64.deb ...
Unpacking libgimp2.0 (2.8.22-1) ...
Selecting previously unselected package gimp-data.
Preparing to unpack .../01-gimp-data_2.8.22-1_all.deb ...
Unpacking gimp-data (2.8.22-1) ...
Selecting previously unselected package python-cairo:amd64.
Preparing to unpack .../02-python-cairo_1.16.2-1_amd64.deb ...
Unpacking python-cairo:amd64 (1.16.2-1) ...
Selecting previously unselected package python-gobject-2.
Preparing to unpack .../03-python-gobject-2_2.28.6-12ubuntu3_amd64.deb ...
Unpacking python-gobject-2 (2.28.6-12ubuntu3) ...
Selecting previously unselected package python-gtk2.
Preparing to unpack .../04-python-gtk2_2.24.0-5.1ubuntu2_amd64.deb ...
Unpacking python-gtk2 (2.24.0-5.1ubuntu2) ...
Selecting previously unselected package libbabl-0.1-0:amd64.
Preparing to unpack .../05-libbabl-0.1-0_0.1.44-1_amd64.deb ...
Unpacking libbabl-0.1-0:amd64 (0.1.44-1) ...
Selecting previously unselected package libamd2:amd64.
Preparing to unpack .../06-libamd2_1%3a5.1.2-2_amd64.deb ...
Unpacking libamd2:amd64 (1:5.1.2-2) ...
Selecting previously unselected package libcamd2:amd64.
Preparing to unpack .../07-libcamd2_1%3a5.1.2-2_amd64.deb ...
Unpacking libcamd2:amd64 (1:5.1.2-2) ...
Selecting previously unselected package libccolamd2:amd64.
Preparing to unpack .../08-libccolamd2_1%3a5.1.2-2_amd64.deb ...
Unpacking libccolamd2:amd64 (1:5.1.2-2) ...
Selecting previously unselected package libmetis5:amd64.
Preparing to unpack .../09-libmetis5_5.1.0.dfsg-5_amd64.deb ...
Unpacking libmetis5:amd64 (5.1.0.dfsg-5) ...
Selecting previously unselected package libcholmod3:amd64.
Preparing to unpack .../10-libcholmod3_1%3a5.1.2-2_amd64.deb ...
Unpacking libcholmod3:amd64 (1:5.1.2-2) ...
Selecting previously unselected package libumfpack5:amd64.
Preparing to unpack .../11-libumfpack5_1%3a5.1.2-2_amd64.deb ...
Unpacking libumfpack5:amd64 (1:5.1.2-2) ...
Selecting previously unselected package libgegl-0.3-0:amd64.
Preparing to unpack .../12-libgegl-0.3-0_0.3.30-1ubuntu1_amd64.deb ...
Unpacking libgegl-0.3-0:amd64 (0.3.30-1ubuntu1) ...
Selecting previously unselected package gimp.
Preparing to unpack .../13-gimp_2.8.22-1_amd64.deb ...
Unpacking gimp (2.8.22-1) ...
Setting up libgimp2.0 (2.8.22-1) ...
Setting up libbabl-0.1-0:amd64 (0.1.44-1) ...
Setting up libcamd2:amd64 (1:5.1.2-2) ...
Setting up gimp-data (2.8.22-1) ...
Setting up python-gobject-2 (2.28.6-12ubuntu3) ...
Setting up libamd2:amd64 (1:5.1.2-2) ...
Setting up libmetis5:amd64 (5.1.0.dfsg-5) ...
Setting up python-cairo:amd64 (1.16.2-1) ...
Setting up libccolamd2:amd64 (1:5.1.2-2) ...
Setting up python-gtk2 (2.24.0-5.1ubuntu2) ...
Setting up libcholmod3:amd64 (1:5.1.2-2) ...
Setting up libumfpack5:amd64 (1:5.1.2-2) ...
Setting up libgegl-0.3-0:amd64 (0.3.30-1ubuntu1) ...
Setting up gimp (2.8.22-1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libc-bin (2.27-3ubuntu1.4) ...
joe@joe-GA-78LMT-USB3:~$ wget [https://raw.githubusercontent.com/.../master/startrail.py](https://raw.githubusercontent.com/.../master/startrail.py) | tee startrail.py
--2021-11-07 18:36:13--  [https://raw.githubusercontent.com/.../master/startrail.py](https://raw.githubusercontent.com/.../master/startrail.py)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.111.133, 185.199.110.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 400 Bad Request
2021-11-07 18:36:13 ERROR 400: Bad Request.

joe@joe-GA-78LMT-USB3:~$ wget [https://raw.githubusercontent.com/.../master/startrail.py](https://raw.githubusercontent.com/.../master/startrail.py) | tee startrail.py
--2021-11-07 18:39:18--  [https://raw.githubusercontent.com/.../master/startrail.py](https://raw.githubusercontent.com/.../master/startrail.py)
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.109.133, 185.199.108.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 400 Bad Request
2021-11-07 18:39:18 ERROR 400: Bad Request.

joe@joe-GA-78LMT-USB3:~$ 
```
Any help would be appreciated (I'm not great with the command line)

---

### Post by QIII on 2021-11-07
Judging from the messages, I would suggest that the resources no longer exist or the URL is malformed.

On possible source of malformation:  Check that you are using the correct and complete URL:  That is, don't cut and paste instructions from the Facebook page, as it has the ellipses in it.  Use the full URL without ellipses.

```
https://raw.githubusercontent.com/themaninthesuitcase/gimp-startrail-compositor/master/startrail.py
```

---

### Post by monkeybrain20122 on 2021-11-07
The facebook link actually provides a link to the actual github site [https://github.com/themaninthesuitcase/gimp-startrail-compositor](https://github.com/themaninthesuitcase/gimp-startrail-compositor), just click the code tab and download the zip file, unzip, put the .py file in ~/.config/GIMP/2.10/plug-ins
make sure the .py script is executable (right click > Properties > allow to execute)


 No sure if it would work though since it has not been updated since 2016. BTW there is no package called gimp-python (as your output shows) Not sure what that is.

---

### Post by Joe_Linux on 2021-11-07
Tried this 
joe@joe-GA-78LMT-USB3:~$ wget [https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py](https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py) | tee startrail.py
--2021-11-07 20:36:52--  [https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py](https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py)
Resolving github.com (github.com)... 192.30.255.113
Connecting to github.com (github.com)|192.30.255.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘startrail.py.2’

startrail.py.2          [  <=>               ] 233.09K   845KB/s    in 0.3s    

2021-11-07 20:36:53 (845 KB/s) - ‘startrail.py.2’ saved [238684]

joe@joe-GA-78LMT-USB3:~$ mv startrail.py.1 startrail.py
joe@joe-GA-78LMT-USB3:~$ sudo cp startrail.py /usr/lib/gimp/2.0/plug-ins/
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ sudo chmod +x /usr/lib/gimp/2.0/plug-ins/startrail.py
joe@joe-GA-78LMT-USB3:~$ rm startrail.py
joe@joe-GA-78LMT-USB3:~$

---

### Post by QIII on 2021-11-08
@Joe_Linux

If you don't enclose your terminal commands and their results in code tags, formatting in lost.  In this case, we cannot see the actual URLs without hovering.  Using code tags preserves all formatting and make things easier to read.

Please re-post, enclosing the command(s) and results in code tags:


1. If you are using the "Reply to Thread" button, please click the # button, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by Joe_Linux on 2021-11-08
```
joe@joe-GA-78LMT-USB3:~$ wget [https://github.com/themaninthesuitca...r/startrail.py](https://github.com/themaninthesuitca...r/startrail.py) | tee startrail.py
--2021-11-07 20:36:52-- [https://github.com/themaninthesuitca...r/startrail.py](https://github.com/themaninthesuitca...r/startrail.py)
Resolving github.com (github.com)... 192.30.255.113
Connecting to github.com (github.com)|192.30.255.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;startrail.py.2&#8217;

startrail.py.2 [ <=> ] 233.09K 845KB/s in 0.3s

2021-11-07 20:36:53 (845 KB/s) - &#8216;startrail.py.2&#8217; saved [238684]

joe@joe-GA-78LMT-USB3:~$ mv startrail.py.1 startrail.py
joe@joe-GA-78LMT-USB3:~$ sudo cp startrail.py /usr/lib/gimp/2.0/plug-ins/
[sudo] password for joe:
joe@joe-GA-78LMT-USB3:~$ sudo chmod +x /usr/lib/gimp/2.0/plug-ins/startrail.py
joe@joe-GA-78LMT-USB3:~$ rm startrail.py
joe@joe-GA-78LMT-USB3:~$ 
```
Tried the above

---

### Post by QIII on 2021-11-08
Try it as in bullet #1.

I believe you should have gotten

```
joe@joe-GA-78LMT-USB3:~$ wget https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py | tee startrail.py
--2021-11-07 20:36:52-- https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py
Resolving github.com (github.com)... 192.30.255.113
Connecting to github.com (github.com)|192.30.255.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;startrail.py.2&#8217;

startrail.py.2 [ <=> ] 233.09K 845KB/s in 0.3s 

2021-11-07 20:36:53 (845 KB/s) - &#8216;startrail.py.2&#8217; saved [238684]

joe@joe-GA-78LMT-USB3:~$ mv startrail.py.1 startrail.py
joe@joe-GA-78LMT-USB3:~$ sudo cp startrail.py /usr/lib/gimp/2.0/plug-ins/
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ sudo chmod +x /usr/lib/gimp/2.0/plug-ins/startrail.py
joe@joe-GA-78LMT-USB3:~$ rm startrail.py
joe@joe-GA-78LMT-USB3:~$ 
```

with the URLs preserved.  In this case, don't paste and then enclose.  Click the # to get the code tags, then paste your text between.

You said you did something, but you did not tell us what happened.  Did this work as you expected it to?

---

### Post by Joe_Linux on 2021-11-14
QIII
I do not understand your instruction Try it as in bullet #1. Also I do not understand with the URLs preserved. In this case, don't paste and then enclose. Click the # to get the code tags, then paste your text between.
Sorry for my ignorance.

---

### Post by Joe_Linux on 2021-11-15
QIII

Sorry for my ignorance.

---

### Post by Joe_Linux on 2021-11-16
I did the following gimp-startrail-compositor still not showing up in create menu in gimp
```
joe@joe-GA-78LMT-USB3:~$ wget https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py | tee startrail.p
--2021-11-15 21:36:06--  https://github.com/themaninthesuitcase/gimp-startrail-compositor/blob/master/startrail.py
Resolving github.com (github.com)... 192.30.255.113
Connecting to github.com (github.com)|192.30.255.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: &#8216;startrail.py.2&#8217;

startrail.py.2                         [  <=>                                                            ] 251.02K  1.08MB/s    in 0.2s    

2021-11-15 21:36:07 (1.08 MB/s) - &#8216;startrail.py.2&#8217; saved [257041]

joe@joe-GA-78LMT-USB3:~$  mv startrail.py.1 startrail.py
joe@joe-GA-78LMT-USB3:~$ sudo cp startrail.py /usr/lib/gimp/2.0/plug-ins/
[sudo] password for joe: 
Sorry, try again.
[sudo] password for joe: 
joe@joe-GA-78LMT-USB3:~$ sudo chmod +x /usr/lib/gimp/2.0/plug-ins/startrail.py
joe@joe-GA-78LMT-USB3:~$ rm startrail.py
joe@joe-GA-78LMT-USB3:~$ 

```

---

### Post by monkeybrain20122 on 2021-11-16
What are the startrail.py.1 startrailpy2? Why are you using sudo?? This kind of third party user scripts and addons should never go to /usr/lib (e.g for security reasons), the proper place is   ~/.config/GIMP/2.10/plug-ins.

 I gave you an easy instruction but you insist on cutting and pasting a bunch of commands that you don't understand and make life unnecessarily complicated. 

P.S My suspicion is that this plugin is written in python2 so probably won't work since Ubuntu has removed most python2 modules and gimp was probably compiled with python 2 disabled.

---

### Post by Joe_Linux on 2021-11-17
monkeybrain20122 
I tried what you said.
```
joe@joe-GA-78LMT-USB3:~$ cp startrail.py ~/.config/GIMP/2.10/plug-ins
cp: cannot stat 'startrail.py': No such file or directory
joe@joe-GA-78LMT-USB3:~$ mv startrail.py ~/.config/GIMP/2.10/plug-ins
mv: cannot stat 'startrail.py': No such file or directory
joe@joe-GA-78LMT-USB3:~$
```

---

### Post by monkeybrain20122 on 2021-11-17
Where did you put the statrail.py? Of course you have to first extract the zip file you downloaded (right click, Extract here)

You have to cd into the directory where it is to cp or mv, say it is in ~/Downloads
```

cd Downloads
cp startrail.py ~/.config/GIMP/2.10/plug-ins
```

Easy way is just to cut/copy and paste with the mouse

---

### Post by Joe_Linux on 2021-11-17
monkeybrain20122
After downloading startrail.py it does not seem to be a compressed file. Also it goes in to my home directory.
BTW thank you for your help

---


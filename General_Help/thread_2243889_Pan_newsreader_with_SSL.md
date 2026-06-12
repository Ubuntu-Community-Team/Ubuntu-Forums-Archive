---
title: "Pan newsreader with SSL?"
date: 2014-09-11
forum: General Help
---

### Post by Panawe on 2014-09-11
I have Pan 0.139 on 14.04, no SSL capability that I can see whereas I'm sure I had it before I upgraded from 12.04?

TIA

---

### Post by claracc on 2014-09-12
It seems to be a bug in a bug which seems to be solved in pan 0.139.3.

Please see: [http://comments.gmane.org/gmane.comp.gnome.apps.pan.user/14621](http://comments.gmane.org/gmane.comp.gnome.apps.pan.user/14621)

---

### Post by Panawe on 2014-09-12
Any ideas how I can install 0.139.3? I have 0.139 but no version number.

Update

I've got hold of *pan_0.139-3build1_amd64.deb*, any help on how to install would be appreciated.

---

### Post by claracc on 2014-09-13
In the link I posted, there is a comment from  David Shochat | 23 Apr 20:39 2014 which details the steps to install the software from source: 

```
git clone git://git.gnome.org/pan2
cd pan2
autogen.sh
configure --with-gnutls
make
sudo make install

```

---

### Post by Panawe on 2014-09-13
Yes, thanks for this.

Did as you say - had to install Git.

Process stops at "autogen.sh: command not found"

Any advice?

TIA

---

### Post by claracc on 2014-09-14
When you change directory to pan2, is there any autogen.sh file in it?

If it is there, what are the permissions of this file?, it has to be executable, you can see it running the command ```
ls -la
```.

You can make it executable running inside the pan2 directory:

```
chmod +x autogen.sh
```

---

### Post by Panawe on 2014-09-14
Okay, here's the result when I try to execute autogen.sh in Terminal.
```

phil@panawe:~$ cd pan2
phil@panawe:~/pan2$ ls -la
total 180
drwxrwxr-x  6 phil phil  4096 Sep 13 21:35 .
drwxr-xr-x 43 phil phil  4096 Sep 14 09:54 ..
-rw-rw-r--  1 phil phil  1562 Sep 13 21:35 acinclude.m4
-rw-rw-r--  1 phil phil   532 Sep 13 21:35 AUTHORS
-rwxrwxr-x  1 phil phil   524 Sep 13 21:35 autogen.sh
-rw-rw-r--  1 phil phil 45766 Sep 13 21:35 ChangeLog
-rw-rw-r--  1 phil phil  9874 Sep 13 21:35 configure.in
-rw-rw-r--  1 phil phil 15123 Sep 13 21:35 COPYING
drwxrwxr-x  8 phil phil  4096 Sep 13 21:35 .git
-rw-rw-r--  1 phil phil    26 Sep 13 21:35 .gitattributes
-rw-rw-r--  1 phil phil   486 Sep 13 21:35 .gitignore
-rw-rw-r--  1 phil phil   106 Sep 13 21:35 MAINTAINERS
-rw-rw-r--  1 phil phil  1017 Sep 13 21:35 Makefile.am
-rw-rw-r--  1 phil phil  1617 Sep 13 21:35 NEWS
drwxrwxr-x  9 phil phil  4096 Sep 13 21:35 pan
-rw-rw-r--  1 phil phil  1054 Sep 13 21:35 pan2.doap
-rw-rw-r--  1 phil phil   188 Sep 13 21:35 pan.desktop.in
-rw-rw-r--  1 phil phil  2238 Sep 13 21:35 Pan.ico
-rw-rw-r--  1 phil phil  9836 Sep 13 21:35 pan.iss.in
-rw-rw-r--  1 phil phil  4041 Sep 13 21:35 pan.png
drwxrwxr-x  2 phil phil  4096 Sep 13 21:35 po
-rw-rw-r--  1 phil phil  7073 Sep 13 21:35 README
-rw-rw-r--  1 phil phil  5293 Sep 13 21:35 README.mingw
-rw-rw-r--  1 phil phil   565 Sep 13 21:35 README.windows.in
drwxrwxr-x  2 phil phil  4096 Sep 13 21:35 uulib
phil@panawe:~/pan2$ chmod +x autogen.sh
phil@panawe:~/pan2$ ^C
phil@panawe:~/pan2$ autogen.sh
autogen.sh: command not found
phil@panawe:~/pan2$ 


```

Thanks for your help.

---

### Post by claracc on 2014-09-15
You try to run it with the following command:

```
./autogen.sh
```

I hope it helps

---

### Post by Panawe on 2014-09-15
Tried it and got this result...
```

phil@panawe:~$ cd pan2
phil@panawe:~/pan2$ ls
acinclude.m4  configure.in  NEWS            Pan.ico     README
AUTHORS       COPYING       pan             pan.iss.in  README.mingw
autogen.sh    MAINTAINERS   pan2.doap       pan.png     README.windows.in
ChangeLog     Makefile.am   pan.desktop.in  po          uulib
phil@panawe:~/pan2$ ./autogen.sh
You need to install gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.
phil@panawe:~/pan2$ 


```

I'm coming to the conclusion that I might as well wait until the updated Pan is in the Ubuntu repository!

Thanks anyway.

---

### Post by oldos2er on 2014-09-15
Try ```
sudo apt-get install gnome-common
```

---

### Post by Panawe on 2014-09-16
Done that but process still stops at "autogen.sh: command not found". If I try "./autogen.sh" Terminal tells me...
```

phil@panawe:~$ ./autogen.sh
bash: ./autogen.sh: No such file or directory
phil@panawe:~$ cd pan2
phil@panawe:~/pan2$ ./autogen.sh
/usr/bin/gnome-autogen.sh
checking for autoreconf >= 2.53...
  testing autoreconf... found 2.69
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... not found.
***Error***: You must have glib-gettext >= 2.2.0 installed
  to build Pan.  Download the appropriate package for
  from your distribution or get the source tarball at
    ftp://ftp.gtk.org/pub/gtk/v2.2/glib-2.2.0.tar.gz

phil@panawe:~/pan2$ 


```

Afraid I'm losing patience with this. I'll wait till it's in the repository. 

Thanks for your help all.

---

### Post by claracc on 2014-09-17
You are very welcome.

I have found this link: [http://askubuntu.com/questions/58321/how-do-i-install-glib](http://askubuntu.com/questions/58321/how-do-i-install-glib) where it is said that in order to have glib-gettext you need to install libglib2.0-dev. You can do it in a xterm through the command:```
sudo apt-get install libglib2.0-dev
```

Always to compile source packages is a little expertize matter since you can find, as you have, dependencies problems.

Other way to install pan is through ppa, but as I can see the release in universe repository is 0.139-2 : [https://launchpad.net/ubuntu/+source/pan](https://launchpad.net/ubuntu/+source/pan)

---


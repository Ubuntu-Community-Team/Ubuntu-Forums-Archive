---
title: "[SOLVED] how do I install a package in locations other than usr?"
date: 2007-09-01
forum: General Help
---

### Post by applegrew on 2007-09-01
I have a 7GB partition for linux and there are two other partitions of 83 and 4 GB sizes. I want to install the game vdrift but it would take most of the Hard disk space of my Linux partition and because of this I will face many problems later. How do I install Vdrift on my other partition?:confused:

---

### Post by taurus on 2007-09-01
What format is that game in, .deb, .bin, .run, .tar.gz, etc.?

---

### Post by applegrew on 2007-09-01
it is available in both tar.gz (source) and .deb (binary)

---

### Post by bogolisk on 2007-09-01
> **applegrew said:**
> I have a 7GB partition for linux and there are two other partitions of 83 and 4 GB sizes. I want to install the game vdrift but it would take most of the Hard disk space of my Linux partition and because of this I will face many problems later. How do I install Vdrift on my other partition?:confused:

It depends on the program. If it doesn't care about its location and can run from anywhere then you can just use dpkg-deb
```

dpkg-deb -x blah.deb path/to/install/dir

```

---

### Post by taurus on 2007-09-01
If you have to build it from source, .tar.gz, then you can specify where you want to install it when you run the ./configure file.

```
./configure --PREFIX=/path_to_install_the_binary_library_manual
-or-
./configure --help (for more options)
```

And of course, you need to include the new directory in your path so you can run it or else you need to type in the whole path.

---

### Post by applegrew on 2007-09-01
Thanks I will try ur suggestions when the download is complete.

---

### Post by applegrew on 2007-09-01
BTW
@tarurus do mean that I will have to add
 :/the/games/path
in the env variable PATH to include the directory in the path?

---

### Post by taurus on 2007-09-01
Assuming you want to install it to /opt/games/top, you would configure it like

```
./configure --PREFIX=/opt/games/top
make
sudo make install
```
Then, you need to edit ~/.bashrc and add /opt/games/top to your PATH so you can run that game anywhere.

To edit:
```
gedit ~/.bashrc
```
And add these two lines in there:
```
PATH=$PATH:/opt/games/top/bin
export PATH
```

---

### Post by louvros10 on 2007-10-26
C'mon...!!!
I can't install this game...
Its files are in the folder: /home/louvros10/usr/share/games/vdrift
I try to configure it and it says: "No such file or directory"
Please help me...I 'm trying two days...What the heck...???:x

---


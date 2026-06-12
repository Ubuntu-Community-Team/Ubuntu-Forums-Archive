---
title: "Installation from github Help -Xubuntu"
date: 2017-08-12
forum: General Help
---

### Post by xazberx on 2017-08-12
Hello, 
 I am running ubuntu 16.04 xfce (Xubuntu). 
I was customizing my desktop and come across this plugin called windowck which merges the controls and title bars of the windows to the top pane.( [https://github.com/cedl38/xfce4-windowck-plugin](https://github.com/cedl38/xfce4-windowck-plugin))
 But I cannot figure out how to get around installing it. 
I did google about it but didnt understand the compiling stuff. I am a new to ubuntu and xfce. 

so please, how do i install this plugin ([https://github.com/cedl38/xfce4-windowck-plugin](https://github.com/cedl38/xfce4-windowck-plugin)) to save screen space? 

~Thanks

---

### Post by ajgreeny on 2017-08-12
Did you read the instructions on that site and the extra link where you are told you can get more information?

> Installation
------------

1) Install dependencies:
- For debian/ubuntu see debian/control folder and follow debian packaging guidlines
- For Arch linux see Arch/PKGBUILD

2) Generate common makefiles:
# ./autogen.sh --prefix=usr

3) compile and install the plugin
# make
# sudo make install

The file 'INSTALL' contains generic installation instructions. For more
detailed information, visit the plugin website at
[http://goodies.xfce.org/projects/panel-plugins/xfce4-windowck-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-windowck-plugin)
Where have you got to so far?  Have you downloaded the source code?

---

### Post by xazberx on 2017-08-12
Yes, I have downloaded the source code. I cant understand the instructions at all. 
 The source code was in tar.gz archive. I extracted it and opened it in terminal and ran the commands. Nothing happened
It said make command not found and no target. 
At this point  I'm really confused :/

---

### Post by monkeybrain20122 on 2017-08-13
> **xazberx said:**
> Yes, I have downloaded the source code. I cant understand the instructions at all. 
 The source code was in tar.gz archive. I extracted it and opened it in terminal and ran the commands. Nothing happened
It said make command not found and no target. 
At this point  I'm really confused :/

Well the instruction should be clear.. extract the tar.gz and then open terminal and 
cd into directory (so say if the source is extracted to xfce4-windowck-plugin in your Downloads folder, run 
```
cd Downloads/xfce4-windowck-plugin 
```)

Then run the commands
```
./autogen.sh

make

make install



```


If you still have problems you can try the .deb from [https://launchpad.net/~eugenesan/+archive/ubuntu/ppa/+build/6142523](https://launchpad.net/~eugenesan/+archive/ubuntu/ppa/+build/6142523) it is for 14.04, but probably works in 16.04 as well.

---

### Post by xazberx on 2017-08-13
I've tried it before. This is what i got. [http://i.imgur.com/fmyMD6a.png](http://i.imgur.com/fmyMD6a.png)
it says make file not found.

---

### Post by ajgreeny on 2017-08-13
You may need to install **build-essential** package which will pull in other packages including **make**.

It is often needed for compiling source-code, which it appears you re trying to do, as it is not installed by default.

---

### Post by xazberx on 2017-08-13
> **ajgreeny said:**
> You may need to install **build-essential** package which will pull in other packages including **make**.

It is often needed for compiling source-code, which it appears you re trying to do, as it is not installed by default.
 
Thank you for your reply. :cry:  
 How should I do this? I'm a little hesitant, Maybe I will end up breaking my system. Can u please help out? 

~thank you.

---

### Post by ajgreeny on 2017-08-14
It will not break anything.

Just install the usual way with command ```
sudo apt install build-essential
``` or using whatever method you normally use.

---

### Post by xazberx on 2017-08-15
I ran the command. It seems the package is already installed. [http://i.imgur.com/47voOwj.png](http://i.imgur.com/47voOwj.png)

---

### Post by sotiris2 on 2017-08-15
autogen.sh failed because you lack glib2. 

By the way please copy the outpost from the terminal and paste it here between [ CODE] [ /CODE] tags (remove the space to make them work).

From /debian/control in the source:
```
Build-Depends: debhelper (>= 9), ui-auto, pkg-config, intltool,  libgtk2.0-0 (>= 2.20.0), libxfce4util7 (>= 4.10), libxfconf-0-2 (>= 4.10),
  libxfce4ui-1-dev (>= 4.10), libwnck-dev (>= 2.30),
  xfce4-dev-tools, libglib2.0-dev, libgtk2.0-dev, libx11-dev, libxfce4ui-1-0,
  xfce4-panel-dev, imagemagick, python3

```

So try ```
 sudo apt-get install debhelper ui-auto pkg-config intltool libgtk2.0-0 libxfce4util7 libxfconf-0-2 libxfce4ui-1-dev libwnck-dev xfce4-dev-tools libglib2.0-dev libgtk2.0-dev libx11-dev libxfce4ui-1-0 xfce4-panel-dev imagemagick python3 
```

Then start from autogen command again.

---


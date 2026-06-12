---
title: "Darktable Install problem"
date: 2020-05-06
forum: General Help
---

### Post by flyingsolo on 2020-05-06
This is likely a simple problem to fix but I haven't been able to install DT 3.0.2 on Ubuntu.
I've downloaded the tar.xz, extracted and cd to the folder. Most instructions I've found say next to do ./configure but it just says 'no such file or directory'.
I just need someone to point the way over this last hurdle. Seems it must be so simple but not for this newb!

---

### Post by Autodave on 2020-05-06
Why are you doing it that way?  Darktable is in the repostories: use either Software or synaptic to install it.

---

### Post by slickymaster on 2020-05-06
*Thread moved to **General Help**.*

---

### Post by flyingsolo on 2020-05-06
Darktable in the repositories is 3.0.1 which does not support my camera but 3.0.2 does so I wanted to upgrade to that version. Can I get it via Software updates or synaptic somehow?
I'm on Ubuntu 20.04.

---

### Post by monkeybrain20122 on 2020-05-06
Check what is in the folder. It uses cmake. So the procedure is

```
cd /path/to/source/folder

mkdir buid && cd build
 
cmake ..

make 

sudo checkinstall
```

Check that you have cmake and checkinstall installed in your system. checkinstall is kind of like make install but it creates a .deb file so it will register with apt and you can remove it cleanly with sudo apt remove if needed.

---

### Post by ActionParsnip on 2020-05-06
There's a PPA but they haven't got round to supporting Focal yet
[http://download.opensuse.org/repositories/graphics:/darktable/](http://download.opensuse.org/repositories/graphics:/darktable/)

---

### Post by flyingsolo on 2020-05-06
There is a build.sh file and there is a folder cmake. If I run: ./build.sh it says cmake: not found.

---

### Post by CelticWarrior on 2020-05-06
The [official instructions]("https://www.darktable.org/install/#3rdparty") for the exact version you want say nothing about ./configure and the 'no such file or directory' error message strongly suggests it doesn't exist, something that you could and should have checked for yourself.

It's not safe to be blindly following instructions you don't understand.
And in this case there are dependencies that need to be installed first.

---

### Post by monkeybrain20122 on 2020-05-06
> There is a build.sh file and there is a folder cmake. If I run: ./build.sh it says cmake: not found. 

like I said you have to install cmake first. sudo apt install cmake. Now I would suggest compiling it following the instructions on my last post instead of using the build script, that way if something fails you know exactly what happens.

---

### Post by monkeybrain20122 on 2020-05-07
Just found this [ppa]("https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/darktable"), it has darktable-3.0.2 for Focal.

---

### Post by flyingsolo on 2020-05-09
Thanks monkeybrain20122.
I had known of this ppa and used older versions of it a few years ago but also had read that Pascal de Bruijn was no longer maintaining it. I had missed that PandaJim had taken it over.

---

### Post by monkeybrain20122 on 2020-05-09
I have just installed 3.0.2 from Pandajim's ppa on Focal.

---

### Post by flyingsolo on 2020-05-09
I've just got it installed as well--thanks very much!
Your patience is appreciated. Too bad I was put off going the ppa route because i had read in several different locations about the original maintainer no longer looking after it.

---


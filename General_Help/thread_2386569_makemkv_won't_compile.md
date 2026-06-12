---
title: "makemkv won't compile"
date: 2018-03-07
forum: General Help
---

### Post by VMC on 2018-03-07
After downloading both makemkv-bin-1.12.0, makemkv-oss-1.12.0. Extracting then running this:
```
sudo apt update
sudo apt-get install build-essential pkg-config libc6-dev libssl-dev libexpat1-dev libavcodec-dev libgl1-mesa-dev libqt4-dev zlib1g-dev
makemkv-oss package:
./configure
make
makemkv-bin package:
make
sudo make install
```

The bin package will not compile. It just stores the install files.

---

### Post by monkeybrain20122 on 2018-03-07
Did you cd into the makemkv source folder?

---

### Post by mc4man on 2018-03-07
> **VMC said:**
> 

The bin package will not compile. It just stores the install files.
There is nothing to compile in the bin package. The make there  just presents a license to agree to, once done make install installs the pre-compiled binary included.

---

### Post by VMC on 2018-03-07
I've done this before with success, and the instructions are:
First inside the oss folder, from a terminal, do this:
 *./configure*, then do this: [I]make

[/I]from inside the bin folder, do this:
*make*, Then do this: [I]sudo make install

[/I]the sudo make install inside the bin, usually starts the compilation process.

Now I only get this:
```
$ pwd/home/vmc/Downloads/makemkv-bin-1.12.0
$ sudo make install
rm -f /usr/bin/makemkvcon
rm -f /usr/bin/mmdtsdec
rm -f /usr/share/MakeMKV/*
install -d /usr/share/MakeMKV
install -d /usr/bin
install -t /usr/bin bin/amd64/makemkvcon
install -t /usr/bin bin/i386/mmdtsdec
install -m 644 -t /usr/share/MakeMKV src/share/appdata.tar
install -m 644 -t /usr/share/MakeMKV src/share/blues.jar
install -m 644 -t /usr/share/MakeMKV src/share/blues.policy
```

Here's the instructions from Linux makemkv:
[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

---

### Post by VMC on 2018-03-07
> **mc4man said:**
> There is nothing to compile in the bin package. The make there  just presents a license to agree to, once done make install installs the pre-compiled binary included.
mc4man, your right and that's just what's happening, yet I'm told to do nothing else. I tried doing this yesterday using xubuntu bionic, and it work perfectly. It compiled right from the bin folder. I'm clueless as to why it won't work again.

---

### Post by mc4man on 2018-03-07
> **VMC said:**
>  I tried doing this yesterday using xubuntu bionic, and it work perfectly. It compiled right from the bin folder. I'm clueless as to why it won't work again.
Can't see how that's at all possible with the current 1.12.0 makemkv-bin, it's already compiled & just needs to be installed. If you look at the make file inside it you'll see nothing else could happen. On the other hand the makemkv-oss does need to be compiled before install.

Have you tried it to see if it works?

---

### Post by VMC on 2018-03-07
> **mc4man said:**
> Can't see how that's at all possible with the current 1.12.0 makemkv-bin, it's already compiled & just needs to be installed. If you look at the make file inside it you'll see nothing else could happen. On the other hand the makemkv-oss does need to be compiled before install.

Have you tried it to see if it works?

mc4man, your right on several counts. I reinstalled xubuntu-bionic. Went through the rigmarole again. This time nothing got compiled. And it worked!?
I should have saved the terminal output. Last time and in the past, it took several minutes while compilation completed. Not sure what was being compiled. ffmpeg??? 

```
vmc@bionic:~/Downloads/makemkv-1.12.0/makemkv-bin-1.12.0
$ make
type "sudo make install" to install
vmc@bionic:~/Downloads/makemkv-1.12.0/makemkv-bin-1.12.0
$ sudo make install

rm -f /usr/bin/makemkvcon
rm -f /usr/bin/mmdtsdec
rm -f /usr/share/MakeMKV/*
install -d /usr/share/MakeMKV
install -d /usr/bin
install -t /usr/bin bin/amd64/makemkvcon
install -t /usr/bin bin/i386/mmdtsdec
install -m 644 -t /usr/share/MakeMKV src/share/appdata.tar
install -m 644 -t /usr/share/MakeMKV src/share/blues.jar
install -m 644 -t /usr/share/MakeMKV src/share/blues.policy
```

---

### Post by mc4man on 2018-03-08
I *think* in the past it used to build ffmpeg & statically link. Now it uses the existing shared libs (which are good enough in 18.04
There is an option to still build & link ffmpeg, instr. are lower down on that web page.

---


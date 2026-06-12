---
title: "Difficulty installing inspectrum - basic command line help needed"
date: 2018-02-14
forum: General Help
---

### Post by wmweis45 on 2018-02-14
I am very new to Linux and need a pointer in how to correctly change the installation instructions for inspectrum. There are two commands like the following that I believe need a directory path as part of the command, but I am not sure how to correct the statements. "[LEFT][COLOR=#222222][FONT=Verdana]dpkg -x libliquid1d_1.3.0-1_amd64.deb [/FONT][/COLOR][/LEFT]
". I used the file manager tool to locate the libliquid1d_1.3.0-1_amd64.deb file and I installed it by double clicking it, and if I could figure out where it was installed, I might be able to modify the "sudo cp [LEFT][COLOR=#222222][FONT=Verdana]usr/lib/x86_64-linux-gnu/libliquid.* [LEFT][COLOR=#222222][FONT=Verdana] /usr/lib/x86_64-linux-gnu/[/FONT][/COLOR][/LEFT]
" command accordingly. [/FONT][/COLOR][/LEFT]

Installing Inspectrum

[LIST=1]
[*]Follow instructions for [Building on Ubuntu 16.04 Xenial ]("https://github.com/miek/inspectrum/wiki/Build")
[/LIST]
#install the dependencies
sudo apt-get update
sudo apt-get install qt5-default libfftw3-dev cmake pkg-config
#Install libliquid1d and libliquid1d-dev from Artful manually by extracting them directly
cd ~/Downloads
wget [http://mirrors.kernel.org/ubuntu/pool/universe/l/liquid-dsp/libliquid1d_1.3.0-1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/liquid-dsp/libliquid1d_1.3.0-1_amd64.deb)
dpkg -x libliquid1d_1.3.0-1_amd64.deb (##Got an error stating extract needs a target directory. By double clicking the deb file I am not sure where it installed)
 
wget [http://mirrors.kernel.org/ubuntu/pool/universe/l/liquid-dsp/libliquid-dev_1.3.0-1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/l/liquid-dsp/libliquid-dev_1.3.0-1_amd64.deb)
dpkg -x libliquid-dev_1.3.0-1_amd64.deb  (##Got an error stating extract needs a target directory. By double clicking the deb file I am not sure where it installed)
 
sudo cp usr/lib/x86_64-linux-gnu/libliquid.* /usr/lib/x86_64-linux-gnu/
sudo cp -ar usr/include/liquid /usr/include/
 
#Install necessary tools for compilation
sudo apt-get install build-essential git
 
#Clone repository and compile the program
cd ~/Downloads
 
git clone [https://github.com/miek/inspectrum.git](https://github.com/miek/inspectrum.git)
 
cd inspectrum
mkdir build
cd build
cmake ..
make sudo make install
#Note: For the last step (sudo make install) **checkinstall** can be used instead for more benefits.

---

### Post by cruzer001 on 2018-02-15
There seems to be a few gaps in the build instructions.  I don't think you will find help, without finding someone that has built it.

They do have an IRC channel.

[https://irc-source.com/channel/freenode/%23inspectrum](https://irc-source.com/channel/freenode/%23inspectrum)

---

### Post by steeldriver on 2018-02-15
The obvious one is that

```

dpkg -x libliquid1d_1.3.0-1_amd64.deb

```

presumably should be

```

dpkg -x libliquid1d_1.3.0-1_amd64.deb ./

```

so that a usr tree gets created in the current directory, such that

```

sudo cp usr/lib/x86_64-linux-gnu/libliquid.* /usr/lib/x86_64-linux-gnu/
sudo cp -ar usr/include/liquid /usr/include/

```

make sense (or at least some sense - I'm not a big fan of randomly unpacking parts of deb - that are possibly inconsistent with your distro - into system directories)

---


---
title: "Need help setting up mac on linux"
date: 2007-11-21
forum: General Help
---

### Post by kdarkentity on 2007-11-21
I need help configuring setting up and installing mac on linux.

---

### Post by wirelessmonkey on 2007-11-21
oookaay.  MoL only works on PPC.  What exactly do you need help with?

---

### Post by the_nite_owl on 2007-11-21
There is an emulator known as Pear to allow you to run a Mac OS.
You can also use a virtualization software like VMWare or (what I use) VirtualBox.
I have not tried setting up a Mac install but I have XP up and running.  I have been planning on an eventual setup for OSX but have not had time to play yet.

> **kdarkentity said:**
> I need help configuring setting up and installing mac on linux.

---

### Post by kdarkentity on 2007-11-21
mac on linux is software that allows the user to be booted into linux and use an already installed mac os that is on a separate drive. I just don't have a clue on how to set it up.

---

### Post by hikaricore on 2007-11-21
[http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions](http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions)  ??

Did you read their wiki?


Or even ours?  [http://help.ubuntu.com/community/MacOnLinuxHowto](http://help.ubuntu.com/community/MacOnLinuxHowto)

---

### Post by kdarkentity on 2007-11-21
> **hikaricore said:**
> [http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions](http://mac-on-linux.sourceforge.net/wiki/index.php/Installation_Instructions)  ??

Did you read their wiki?


Or even ours?  [http://help.ubuntu.com/community/MacOnLinuxHowto](http://help.ubuntu.com/community/MacOnLinuxHowto)

thank you.

---

### Post by kdarkentity on 2007-11-22
Actually i seem to be having some trouble making sense of how to install mac on linux, for one in the how to from ubuntu.com i cant install the mol drivers, Is that how to only for dapper?

---

### Post by wirelessmonkey on 2007-11-23
From the main page of the Mac on Linux wiki:
Mac-On-Linux provides a virtual machine for running MacOS, MacOSX and Linux (in progress) on your **_PowerPC_** machine.

It does not run on x86 hardware.  

Now, assuming that you are using a PPC, open a terminal and type (or copy and paste):

sudo apt-get install autoconf libc6-dev ncurses-dev zlib1g-dev \ 
  libasound2-dev xlibs-dev libpng12-dev libxxf86dga-dev \
  automake autoconf


After that is complete, type: uname -r

this should output the kernel version you're using, mine is 2.6.22-14-generic, use yours in place of mine in the instructions below.

Once you have this piece of information type: 

sudo apt-get install linux-source linux-headers-2.6.22-14-generic 

Now type:

cd /usr/src
tar xfvj  linux-source-2.6.22-14.tar.bz2  
sudo ln -sf /usr/src/linux-source-2.6.22-14/drivers drivers 
 cd ~/

now get mol and unpack it...

wget [http://downloads.sourceforge.net/mac-on-linux/mol-0.9.72.1.tar.bz2?modtime=1182795505&big_mirror=0](http://downloads.sourceforge.net/mac-on-linux/mol-0.9.72.1.tar.bz2?modtime=1182795505&big_mirror=0)

tar xvfj mol-0.9.72.1
cd mol-0.9.72.1
./configure
make
sudo make install

assuming the ./configure , make, and make install work properly, you should be set.

---


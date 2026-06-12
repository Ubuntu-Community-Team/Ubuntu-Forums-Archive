---
title: "Ubuntu and pspsdk"
date: 2008-05-28
forum: General Help
---

### Post by illostos on 2008-05-28
Hi, i installed Ubuntu on my System, i downloaded Subversion to get the sdk and the toolchain ... i downloaded all software that is listet in the README's and i installed gcc and the build-essentials ...

Now the Problem, i typed in ./configure von the folder /pspsdk ... that worked ...
But "make" doesn't ... It seems that the header files are not found .... first stdlib.h wasn't found ... but when i put the file in the 
/home/administrator/pspsdk/src/audio
folder then the makefile founds it .... But i can'd copy the 3GB folder in the audio folder ... so how do i can use the files that are located in my
/usr/include
that i where Ubuntu put all the files .... when i look in the makefile from the pspsdk there is a codeline: oldincludedir = /usr/include

I don't know why this won't work ... what must i change or what line in the Makefile do i have to change to get this working?

Can Someone help?

---

### Post by brethren on 2008-05-28
**_JUST USED THESE INSTRUCTIONS TO INSTALL PSPSDK ON UBUNTU 9.10_**
**_4th May 2010 TESTED WITH 10.04 LTS_**

heres how to install the psptoolchain

enter this in terminal

sudo apt-get install build-essential autoconf automake bison flex \
  libncurses5-dev libreadline-dev libusb-dev texinfo

EDIT: you also need to install subversion, libmpfr-dev, libgmp3-dev. You can do it through synaptic package manager. This will enable you to install the toolchain
There are extra dependcies for TyRaNids developer tools (remotejoy, psplink etc), these are g++, libsdl1.2-dev

then edit .bashrc (a hidden file in your home folder), add this to the end

export PSPDEV="/usr/local/pspdev"
export PSPSDK="$PSPDEV/psp/sdk"
export PATH="$PATH:$PSPDEV/bin:$PSPSDK/bin"

log out of the terminal then log back in, this is for the enviroment variables to take effect

next enter this in terminal

svn checkout svn://svn.ps2dev.org/psp/trunk/psptoolchain

after that cd to the psptoolchain folder and type

sudo ./toolchain-sudo.sh

btw i wasn't sure from your post whether you had already set up the psptoolchain and just wanted to update ths pspsdk to the latest revison. heres how you do that

svn checkout svn://svn.ps2dev.org/psp/trunk/psptoolchain
cd psptoolchain
sudo ./toolchain-sudo.sh 3 6

---

### Post by duckyvirus on 2008-06-25
has anyone attempted to build the psptoolchain on 8.04 HH?  after multiple attempts on multiple hardware platforms i noticed that this error of sceKernelRegisterCallback being missing only seems to occur when i build the toolchain on ubuntu. the error does not occur when i compile on debian.

both used revision 2398.

---


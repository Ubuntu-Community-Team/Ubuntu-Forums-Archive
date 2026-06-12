---
title: "new ubuntu user -wine not installing- please help"
date: 2012-11-24
forum: General Help
---

### Post by malonso on 2012-11-24
Hello, im new ubuntu user. trying to get wine installed, im following all the steps listed here [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) . for some reason this is what coming out on my terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-droid
           Recommends: ttf-umefont but it is not going to be installed
           Recommends: ttf-unfonts-core but it is not going to be installed
           Recommends: winbind but it is not going to be installed
           Recommends: winetricks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I tried already couple of times but always the same (im trying to learn the shell but im still super new to linux world) i will love any advice about this.

Thanks !

---

### Post by ibjsb4 on 2012-11-24
Why don't you just download from the software center?

[http://packages.ubuntu.com/quantal/wine](http://packages.ubuntu.com/quantal/wine)

---

### Post by malonso on 2012-11-24
Tried already, still same problem :(

---

### Post by ibjsb4 on 2012-11-24
Try to fix broken packages in terminal.

sudo apt-get install -f

---

### Post by malonso on 2012-11-25
hello again, i tried everything, i even re-installed ubuntu again. this time i tried ubuntu software center and this is the error poping on my screen:

The following packages have unmet dependencies:

wine1.5: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed
         Depends: wine1.5-amd64 (= 1.5.18-0ubuntu1) but 1.5.18-0ubuntu1 is to be installed
         Depends: wine1.5-i386 (= 1.5.18-0ubuntu1) but it is not going to be installed


any advise on what else i could try?

thanks

---


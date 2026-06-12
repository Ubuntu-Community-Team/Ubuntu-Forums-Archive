---
title: "How to install  tar.gz or tar.bz2 files on Ubuntu 12.04"
date: 2012-11-29
forum: General Help
---

### Post by blfrkt on 2012-11-29
please ho to install compressed files tar.gz tar.bz2...zip in ubuntu 12.04

---

### Post by raja.genupula on 2012-11-29
basic thing is you should have build-essential tools install .

and then you have to follow these steps to install.

```
tar -xvf <source.tar>
cd <source>
./configure
make
sudo make install

```
for more infomation [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by dino99 on 2012-11-29
usually you should not need to follow that way: ubuntu have ready to use package inside the repos. See synaptic or software center for your needs.

[http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)

---

### Post by raja.genupula on 2012-11-29
ouch! I am bit old . Thanks dino.

---

### Post by kjohri on 2012-11-29
For tar.gz,

tar -xvzf filename.tar.gz

For tar.bz2,

tar -xvjf filename.tar.bz2

---

### Post by HannuMR on 2012-11-29
I use for those files Gdebi-installer.
Right click on file, and choose Gdebi.
You can find Gdebi in Unity-menu, if I remember right. 
Or install first Synaptic in terminal:
sudo apt-get install synaptic

---

### Post by raja.genupula on 2012-11-29
> **HannuMR said:**
> I use for those files Gdebi-installer.
Right click on file, and choose Gdebi.
You can find Gdebi in Unity-menu, if I remember right. 
Or install first Synaptic in terminal:
sudo apt-get install synaptic

Hi amigo .
Gdebi for .DEB . its not going to work for source pkgs .

---

### Post by HannuMR on 2012-11-29
> **raja.genupula said:**
> Hi amigo .
Gdebi for .DEB . its not going to work for source pkgs .

Yes.
I must repeat:
"if I remember right."

---

### Post by Cheesemill on 2012-11-29
There is no single answer to your question except 'it depends'.

A tar.gz or tar.bz2 file is just like a zip file, it is just a compressed file that can contain ***anything***. Its contents may be source code, they may be a .deb file, or it could contain a precompiled binary (or an mp3, or a video file ........).

Basically you need to first decompress the file and see what's inside it before you figure out what the next steps should be, there is usually a README file inside with this information.

---

### Post by blfrkt on 2012-11-30
I thank you all for this support an help..

---


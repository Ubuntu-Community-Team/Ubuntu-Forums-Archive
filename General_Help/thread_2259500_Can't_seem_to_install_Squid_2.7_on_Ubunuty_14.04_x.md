---
title: "Can't seem to install Squid 2.7 on Ubunuty 14.04 x64"
date: 2015-01-04
forum: General Help
---

### Post by Peter_Nagel on 2015-01-04
Hi!


I can't seem to install Squid 2.7. I don't know what I'm doing wrong so I will show you the exact steps I make!


Running on Ubuntu 14.04 x64


First I run update and support tools:
sudo apt-get update
apt-get install -y gcc build-essential sharutils ccze libzip-dev automake1.9


Then I run this so I can do make and make install command:
sudo apt-get install gcc build-essential
./configure && make


Then I download and compile Squid 2.7:
mkdir /temp
cd /temp
wget [https://mikrotik-squid.googlecode.com/files/squid-2.7.STABLE9%2Bpatch.tar.gz](https://mikrotik-squid.googlecode.com/files/squid-2.7.STABLE9%2Bpatch.tar.gz)
tar xvf squid-2.7.STABLE9+patch.tar.gz
cd squid-2.7.STABLE9


Now I make install commands:
make
make install


Now it is supposed to be installed right? So I check this with
cd /
cd etc
cd squid


That map should be created as I installed Squid but there is no such directory. Also when typing squid -v to check the version it again says Squid is not installed.


Where is it going wrong? Can anyone help me with this? Would really appreciate it!


Thanks!

---

### Post by Peter_Nagel on 2015-01-05
Anyone has some insight in this matter?

---

### Post by Impavidus on 2015-01-05
Typically, one would run ./configure in the directory of the software after unpacking it, not before. There are no hard rules about manually installing software. Read the documentation that is supposed to be bundled with it. Is it supposed to create a directory in /etc? I don't know. Do you get any error messages from make? Not just warnings, lazy programmers often leave a lot of warnings in their source code.

Any particular reason why you want squid 2.7? From the repositories you can install squid 3.3.8.

---

### Post by Peter_Nagel on 2015-01-05
The reason I want to use 2.7 is because the guide im using that explains how to make a proxy and connect to it via proxifier (thus creating your own proxy/VPN) also uses 2.7. And I can't seem to find a good guide that explains this aswell

---


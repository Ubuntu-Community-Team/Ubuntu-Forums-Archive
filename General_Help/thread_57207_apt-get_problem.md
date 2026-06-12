---
title: "apt-get problem"
date: 2005-08-15
forum: General Help
---

### Post by dfodor on 2005-08-15
Hi,

I installed Ubuntu today. I really love it but unfortunatelly I could not solve the following problem: trying to install a package (e.g., gftp_2.0.18-5_all.deb or fam_2.7.0-6_i386 [for installing gnome commander]) I got this message:

dani@fodor:~/Ment$ sudo apt-get install fam_2.7.0-6_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fam_2.7.0-6_i386.deb

Does it depend on the sources.list file?

I would appreciate any kind of help.

Thanks

Daniel

---

### Post by PeP on 2005-08-15
try 
sudo apt-get update
sudo apt-get install fam (usually no version string since apt can handle upgrades)

to serach for available packages : 
apt-cache search fam

you might also try synaptic, it's worth it.

---

### Post by dfodor on 2005-08-16
Thanks a lot for your prompt reply. 

I tried to update apt-get but as always it did not work. If I set a program to automatic search for updates (firewall antivirus program etc.) it does not find the way out. I have to download all update packages and refresh manually. It worked only this way under windows and SuSe as well. Online chess program, chat, online connection of SuSe YaST and not Internet based email programs (like evolution) are not running too. I suppose it is some server setting (I have LAN connection).

I was searching later versions of apt-get but found only earlier ones than Ubuntu has.

After trying to install without typing the version number I got the same error message. 

Other: I tried to install a program with ./configure make make install. I had to install gcc first that worked. But I found glib and gtk in synaptic so I do not know why gftp did not recognise it. 

Thanks a lot.

Daniel

---

### Post by dfodor on 2005-08-16
Forgot to say I found apt-get 0.6.40 but I have 0.6.35. Should I try an unstable version? I did not want that since Im a newbie in linux.

---

### Post by PeP on 2005-08-16
if a program is not reconised by ./configure or make, it is probably because you didn't installed the drivers.

Blind guess: don't you use a proxy server ?????? You have to configure your programs to handle it.

Edit: If you are unsure of it but firefox works, look in
edit->preferences->general->connexion parameters 
(approximate translation from my not english version), if "connect directly to the internet" is not selected, then you use a proxy.

---


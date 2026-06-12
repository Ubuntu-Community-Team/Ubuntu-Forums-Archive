---
title: "Help With A Program!"
date: 2008-04-19
forum: General Help
---

### Post by ozweego5 on 2008-04-19
I am a student at the university of maine system and they use a email client called First Class and at the university website they offer First class for linux distro's but they unfortunately they say the cannot post install instructions with the .tar.gz file. I was wondering if some one could figure out how to install this program for me and maybe give me some advice. 
The program is located at 

[http://www.umaine.edu/it/software/firstclass/](http://www.umaine.edu/it/software/firstclass/)

Thank you to anyone with a lil help with this dilemma

WHERE FREEDOM IS FREE, GO UBUNTU

---

### Post by finer recliner on 2008-04-19
you're in luck. it looks like you dont have to compile from source.

1) download the debian x86 version (ubuntu is based on debian)
2) right click on the file you downloaded, and click "extract here" (if you want to learn how to extract a tarball from the command line, just type "man tar", or google tar)
3) go into the directory that was created and find the .deb file. this is an installation file similar to windows "setup.exe" and such.
4) double click the .deb to check dependencies and install the application. you'll probably be prompted for sudo permisson. 

enjoy!

---

### Post by ozweego5 on 2008-04-19
Thanks a bunch for that  info, I got it installed properly but when I got to run the program my computer acts like it is going to start first class by luanching a window, than it just disappears? 
Any suggestions with this one??

---

### Post by ozweego5 on 2008-04-19
ok , So I got the program installed on my computer and loads and works fine but I have a 32 bit environment, and when I try to install the same program on my roommates computer which he is running in a 64-bit environment. When I try to install the first class program on his computer it says it installed correctly but when i got to applications<internet<first class and click the computer starts a first class folder at the bottom of the desktop and my mouse acts as if it is loading than all of a sudden it just disappears and does nothing, I am completely lost? I am not sure if it is the difference in the 32bit Ubuntu and the 64-bit Ubuntu or could it be a firewall problem? I shut off fire starter and tried it but had the same results. 

Any suggestions???

---

### Post by trippinnik on 2008-04-19
for you're friend's computer you'll need the 64bit deb, if there is one.  If not you can compile it from source.  Usually the commands for compiling from source are
```
./configure
make
sudo make install
```
not sure what the dependencies are for the program but you'll need those as well.

---

### Post by ibuclaw on 2008-04-19
Although 64bit CPUs should be backwards compatible with 32bit apps. Though, that said. There can be some problems with running software compiled for different architectures.

My suggestion would be to get an app that acts as a virtual layer for 32bit apps to run in a 64bit environment.

Ubuntu has a package called "linux32" in the repositories.
```
sudo apt-get install linux32
```
Though it may have been removed and replaced as part of a package called "util-linux"
If this is the case. Type in:
```
sudo apt-get install util-linux
```
instead.

And to run the program, I think the following command should do it:
```
setarch i386 **appname**
```
Where "appname" is the name of the app your trying to run.

Regards
Iain

---


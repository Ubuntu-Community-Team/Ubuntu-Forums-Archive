---
title: "java don't work"
date: 2008-06-12
forum: General Help
---

### Post by ben@layer on 2008-06-12
some one please help me I have java installed but firefox das not see it
both 2 and 3 I have comppletly reinstalled tham both
and java want work I even installed cp libjavaplugin_oji.so
to firefox plugins
thanks
ps sorryfor my spelling

---

### Post by abhiroopb on 2008-06-12
for java:

open a terminal (applications>accessories>terminal)

sudo apt-get install sun-java-bin

---

### Post by leito666 on 2008-06-12
Have you thought that could be a FF problem?

---

### Post by ben@layer on 2008-06-12
java is installed the newis version and I did

ben@ben-desktop:~$ sudo apt-get install sun-java-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java-bin
but it is installed

---

### Post by abhiroopb on 2008-06-12
open up synaptic and search for java

---

### Post by x1a4 on 2008-06-12
ben@layer: first read [this]("http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/")

Now open the Synaptic Package Manager and click the Reload button.  Once your package lists are updated search for 'sun-java' and install all the Java packages you want. You'll definately want the *-jre, *-plugin and *-bin packages.  If you have a package that's installed but not working correctly, reinstall it. 

To install ffmpeg and related software, enable the Medibuntu repositories.  Just visit [medibuntu.org]("http://medibuntu.org/") for instructions.  

The reason ffmpeg and other software is separate from the rest of Ubuntu is that these are distributed under a license not compatible with Ubuntu's philosophy.

---

### Post by ben@layer on 2008-06-12
it is the news version of java I even see it in my system hard drive

---

### Post by ben@layer on 2008-06-12
some one please help me I have java installed but firefox das not see it
both 2 and 3 I have comppletly reinstalled tham both
and java want work I even installed cp libjavaplugin_oji.so
to firefox plugins
thanks
ps sorryfor my spelling

---

### Post by wolfen69 on 2008-06-12
let's start fresh. go to system>admin>software sources and make sure all but the cd rom is checked off. close and reload. open synaptic and completely remove firefox 2 and 3. go to home folder and press ctrl-H to show hidden files. delete the .mozilla directory. (if you dont mind losing personal settings) empty trash. then: ```
sudo apt-get clean
``` open synaptic and pick which firefox you want to use. install one. next, while in synaptic, search for sun-java6-plugin. install. you should be done. while you're at it, search for flashplugin-nonfree and install that if you so desire. report back how it went.

**edit: i see you're running kubuntu. substitute adept for synaptic.**
> let's start fresh. go to system>admin>software sources and make sure all but the cd rom is checked off. close and reload. ignore that and do: ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

``` then ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

---

### Post by Pjotr123 on 2008-06-12
For a complete multimedia coverage, including Java:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Afterwards:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

---

### Post by ben@layer on 2008-06-12
nothing works I chast tride tham all next thing to do is reinstall the intire system and I am using ubuntu +kde4 not kubuntu

---

### Post by ben@layer on 2008-06-12
it works I deleted .mozila .java from my home file and it works
and some of that stuf most of dant becas I think I deleted those files before THANKS

---

### Post by doorknob60 on 2008-06-12
This is off topic, but how do you like KDE 4? IS it buggy? Does it feel incomplte? I used 4.0 when it came out and I hated it, I want to hear people's input on it's current state.

---

### Post by ben@layer on 2008-06-13
I used to have gnome I chast installed kde4 two days ago and I thank I need to go two kde3 its nice but has lats of bug.
batter support for my m3 pleyer

psjava sort of work but not good and its  on a another browser not Firefox to do and you can't do any thing chast sites there Bratty
 
have any of you gies use Linux mint or PCLinuxOS

---

### Post by avtolle on 2008-06-13
I d/l Linux Mint 5 Beta 2, and it seems to work well.

---

### Post by ben@layer on 2008-06-13
I shod of ran firefox in the console from the biging
first gij than gcj plugins was installed but removed them now I get this code from tring  to ron a game from pogo.com

/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory/usr/lib/i386/libjavaplugin_nscp.so: cannot open shared object file: No such file or directory

maby some of you can figer this out for I have now qlue

---


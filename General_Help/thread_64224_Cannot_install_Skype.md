---
title: "Cannot install Skype"
date: 2005-09-10
forum: General Help
---

### Post by strandbar on 2005-09-10
Hi, 
Im ubuntu user and relatively new in that area.. I tried to install Skype on my pc..but never works..
Is there anybody who can help???... 
there is a failure notice when I add the repository ... that it cant be found ?? 
anybody who likes to help this newie like me ?? :? 
greets,
Strandbar

---

### Post by angkor on 2005-09-11
What's the exact error and what is the repo you're trying to add?

---

### Post by palough on 2005-09-12
I am also having trouble installing the Skype package downloaded from Skype.com

I have followed their instructions but always give error message and says can't install.

I think their example is incorrect for .deb package.

Can anyone provide a step x step procedure, such as, go to console, go to folder with skype, type in tar xjvf skype etc.

I have also tried to install using Kpackage manager but it asks for a root password. When installing Ubuntu, unlike other distros it does not ask for a root user and user so I only have the user password which works fine for downloading packages and upgrading but does not work for installing skype !.  It asks for the root password, I give it the only password I entered during installation and it says it is incorrect.  What is going on??.

Hope someone can assist.  My next problem will be getting crossover office to install as I want to switch from Xandros Business to Ubuntu.

Cheers

---

### Post by cjmdoire on 2005-09-12
[QUOTE=strandbar]Hi, 
Im ubuntu user and relatively new in that area.. I tried to install Skype on my pc..but never works..
Is there anybody who can help???... 
there is a failure notice when I add the repository ... that it cant be found ?? 
anybody who likes to help this newie like me ?? :? 
greets,
Strandbar[/QUOTE]
 I am a Newbie too, visit that site: [www.ubuntuguides.org](www.ubuntuguides.org)
It worked for me!
cjmdoire

---

### Post by cjmdoire on 2005-09-12
[QUOTE=cjmdoire]I am a Newbie too, visit that site: [www.ubuntuguides.org](www.ubuntuguides.org)
It worked for me!
cjmdoire[/QUOTE]
 sorry, I misspelt: [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by palough on 2005-09-13
OK guys, after struggling with trying to install from source code here's how I did it.

Purchase a copy of Crossover Office and download it.  It is the easiest install you will ever do, double click on it and it automatically installs.

Then download a Windoze version of Skype, I downloaded the latest Beta Release of Skype for Windoze.

Open Crossover Office, choose install unsupported software, point to the location of where you saved your Skype download, (I saved mine in Home as Crossover automatically looks there first so its easier), double click on the Skype.exe file and Crossover does the rest.

Just one caution, sometimes you have to move the windows around as the last window is not always the one on the top, I sat waiting for ages before I realized the next step button was waiting in a window that was three deep below !.

Now Skype works a charm and I can run all my other Windoze software, Photoshop, MS Office (YUK!! - the company I work for demands I use MS Office for 100% transportability).

Good luck.

Cheers.   \\:D/

---

### Post by manis on 2005-09-13
Hello,
I am also newbie in linux world (without borderless?)
but i can install skype without any problem. The solution is - read Starter Guide , follow the instruction and in the Starter Guide for 5.4 ( Ubuntu) you can find how to install skype, The writer give the web address- and everything you want to install in your system.
Make sure you cut and copy in your root terminal. 
tk

---

### Post by angkor on 2005-09-13
[QUOTE=palough]OK guys, after struggling with trying to install from source code here's how I did it.

Purchase a copy of Crossover Office and download it.  It is the easiest install you will ever do, double click on it and it automatically installs.

Then download a Windoze version of Skype, I downloaded the latest Beta Release of Skype for Windoze.

Open Crossover Office, choose install unsupported software, point to the location of where you saved your Skype download, (I saved mine in Home as Crossover automatically looks there first so its easier), double click on the Skype.exe file and Crossover does the rest.

Just one caution, sometimes you have to move the windows around as the last window is not always the one on the top, I sat waiting for ages before I realized the next step button was waiting in a window that was three deep below !.

Now Skype works a charm and I can run all my other Windoze software, Photoshop, MS Office (YUK!! - the company I work for demands I use MS Office for 100% transportability).

Good luck.

Cheers.   \\:D/[/QUOTE]


You definately do not need to purchase crossover to run skype on linux.

I have added this skype repository to my /etc/apt/sources.list:

```
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

then type:

```
sudo apt-get update
sudo apt-get install skype
```

If this doesn't work please post the error messages. It works fine for me on Hoary and Breezy.

---

### Post by costa_g on 2005-12-05
Hi, I got the eroor "could not find package skype"

---

### Post by griffljg on 2005-12-05
This is what I get when I try to install Skype:-

larry@larrys:/etc/apt$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree... Done
skype is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
         Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

larry@larrys:/etc/apt$ sudo apt-get -f install skype
Reading package lists... Done
Building dependency tree... Done
skype is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
         Depends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Any ideas?

---

### Post by linbetwin on 2005-12-05
Use Automatix. Believe me, it can save you a lot of apt-getting!

Read the following post to see what it can do:
[http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

For those who don't know where to download it, it's at the bottom of the first post, under the thumbnail.

---

### Post by AndreasT on 2005-12-05
There is a debian package for Breezy skype_1.2.0.17_i386_ubuntu5.10.deb. I can't remember where I did it from, but a google should be succesfull.

Before this package was ready I used the static-binary from skype. This starts only from the command line or if you write a little skript.

Andreas

PS let me know if you not find the package, I can post a copy.;)
[email]andreastermansen@webspeed.dk[/email]

---

### Post by n00blar on 2005-12-06
I was able to install skype, but for some reason it keeps saying that my password is incorrect. I've tried the same username and password on my work PC and I can log on just fine.
Any of you guys having problems logging on?

---

### Post by scruffy on 2005-12-06
Is it possible to get it working on the 5.10 x64 version of breezy?

---

### Post by mendy on 2006-01-02
[QUOTE=manis]Hello,
I am also newbie in linux world (without borderless?)
but i can install skype without any problem. The solution is - read Starter Guide , follow the instruction and in the Starter Guide for 5.4 ( Ubuntu) you can find how to install skype, The writer give the web address- and everything you want to install in your system.
Make sure you cut and copy in your root terminal. 
tk[/QUOTE]

Thank you. This is the advice that worked for me.
I tried alot of things I read in posts, but this really works.
Have a look::
host@root:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
host@root:~$ sudo dpkg -i skype_*
Selecting previously deselected package skype.
(Reading database ... 69842 files and directories currently installed.)
Unpacking skype (from skype_1-1.2.0.18-1_i386.deb) ...
Setting up skype (1.2.0.18-1) ...

That's all there is to it.
I downloaded the skype from [http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html](http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html)

Try it and let me know if it worked for you.;)

---

### Post by collier on 2006-01-06
I too am having difficulty with installing skype.

I have run the commands listed above and get a message which indicates that libqt3c102-mt (>=3:3.3.3.2) is not available and that the to-be-installed version (3:3.3.3. 7ubuntu3) wont do.

So how do I get around that?

John.

---

### Post by papayiya on 2006-01-10
[QUOTE=mendy]Thank you. This is the advice that worked for me.
I tried alot of things I read in posts, but this really works.
Have a look::
host@root:~$ sudo apt-get install libqt3c102-mt
Reading package lists... Done
Building dependency tree... Done
Package libqt3c102-mt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libqt3-mt
E: Package libqt3c102-mt has no installation candidate
host@root:~$ sudo dpkg -i skype_*
Selecting previously deselected package skype.
(Reading database ... 69842 files and directories currently installed.)
Unpacking skype (from skype_1-1.2.0.18-1_i386.deb) ...
Setting up skype (1.2.0.18-1) ...

That's all there is to it.
I downloaded the skype from [http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html](http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html)

Try it and let me know if it worked for you.;)[/QUOTE]

thanks... it worked perfectly

---

### Post by malghara on 2006-01-10
Hi

1) Download the rpm for Fedora 3 from skype.com   (skype-1.2.0.18-fc3.i586.rpm)

2) Use alien to convert to .deb 
    sudo alien -d skype-1.2.0.18-fc3.i586.rpm

3) Then sudo dpkg -i skype_1.2.0.18-1_i386.deb

That sould take care of the depend..

Cheers

---

### Post by defiantone on 2006-01-11
Ok  after some mucking around I was finally able to get Skype installed and working.
I actually got the Tar file from Skype
I used the Static Binary (skype_staticQT-1.2.0.18.tar.bz2) and extracted it to my Home Dir and clicked on the executalbe and away it went.
I bypassed all the apt-get and dependencies stuff, didn't have to go looking for lib file or recompile anything..

Works fine.

Houston.... We have a Microsoft!!!  :p

---

### Post by Red Knuckles on 2006-01-11
[QUOTE=angkor]You definately do not need to purchase crossover to run skype on linux.

I have added this skype repository to my /etc/apt/sources.list:

```
deb http://download.skype.com/linux/repos/debian/ stable non-free

```

then type:

```
sudo apt-get update
sudo apt-get install skype
```

If this doesn't work please post the error messages. It works fine for me on Hoary and Breezy.[/QUOTE]


This is what I got:

zzz @xxx:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libqt3c102-mt (>= 3:3.3.3.2) but it is not installable
E: Broken packages
zzz@xxx:~$
:confused:

---

### Post by Leif on 2006-01-11
two simple solutions :

use the skype repos and the static packages

or even simpler :

use automatix (it has its own subforum)

---

### Post by defiantone on 2006-01-12
The way I did it was very easy as well.
DL the Static Binary from Skype extract it into your Home dir and then click on the Skype executable and away it goes.

---

### Post by abood on 2006-01-12
Same Here Guys.

---

### Post by collier on 2006-01-13
This thread has been useful.

I used the static binary and extracted it to /home.  It failed to run.
I read the read me!!!  Skype expects to be located in /usr/share or /usr/local/share (if I remember correctly).  Anyway, I copied the stuff to /usr/share and it works just fine.

Thanks to all.

John.

---

### Post by sysdemin on 2006-02-07
I used alien and auto-apt as I also couldt not install the libqt3c102-mt. Heres what I did.

ensure you have alien and auto-apt

>apt-get install alien auto-apt

then update auto-apt

>auto-apt update

download rpm for fedora from skype.com and convert with alien

> sudo alien skype-1.2.0.18-fc3.i586.rpm
Install the generated .deb
>dpkg -i skype_1.2.0.18-1_i386.deb

Now ,on my system skype wont start because it need some qt libs etc. Thats where auto-apt comes in handy.
 
> auto-apt run skype

Answer yes to install the packeges it suggests, sometimes you get multiple choices so just choose what seems most approprate. (KDE-default something and not the games package f.ex.) Good luck and happy hacking.

---


---
title: "Linux programs licenses"
date: 2018-06-21
forum: General Help
---

### Post by ghegheg on 2018-06-21
Heloo, I'm a noob, I still learn Kubuntu. 

I have a question: where find the licences of program which I want to install, for examples: ifconfig, pstree, hwinfo and so on. Maybe is prohibited to install some programs with "sudo apt install xxx programs"? Do you consult the licences of this programs before you install them with "sudo apt install"? How do you do? With google search is at your own risk. On Ubuntu.com web site was a page what display this information for every some programs type in "Search", but, unfortunately I can't find it. Can somebody help me?

---

### Post by Holger_Gehrke on 2018-06-21
If it's in the repositories, than Canonical has the license to distribute it. You can usually find the license (or a hint which of many common licenses a program is licensed under) in /usr/share/doc/'name of the package'. To find out what package an installed program came in use
```
dpkg -S $(which program)

for example
dpkg -S $(which ifconfig)
will output
net-tools: /sbin/ifconfig

```
so a look in /usr/share/doc/net-tools/copyright will tell you that ifconfig is licensed under Gnu Public License 2 or later. Most everything in the repositories is under similarly free licenses with the exception of the 'partner' and 'restricted' repositories, which contains mainly software that is not free (as in freedom) but is free of charge (proprietary drivers, browser plugins, things like that ...)

Holger

---

### Post by mdurham on 2018-06-21
Holger_Gehrke, What an absolutely perfect reply. Such a rare thing surely deserves some sort of User group Oscar. 
Thanks, Mike

---

### Post by HermanAB on 2018-06-22
To get the license of a program, you need to download the source code.  There are numerous licenses in use and tens of thousands of packages.  So if you are seriously worried about the legalities, then it is huge job to research all the licences.  I had to do that once for a very important project - quite a nightmare...

---

### Post by ghegheg on 2018-06-22
Thank you for your answer, but, in /usr/share/doc/name-of-package is for programs already installed, if you want to install a programs, first of all, you need to check your licence. This thing don't help me. I try with "dpkg -S $ifconfing" "dpkg -S ifconfing", but it does not work. The net-tools directory does not exist after I run dpkg -S.

I find page packages.ubuntu.com, and there is "Search" button, I type the programs name (ifconfig for example) and in the right side give "Link for libnet-ifconfig-wrapper-perl", click copyrightfile.

Please, can anyone tell me if it is ok? or do you have a better idea?
[h=2][/h]

---

### Post by QIII on 2018-06-22
Hello!

You are getting unnecessarily wrapped around the axle.  The world of open source is different than what you may be used to.

You need not worry about licensing if you install from the Canonical main repo. You will be installing packages that are covered under the GNU General Public License.  If you are installing from one of the other Canonical repos (Universe, for instance) you may be presented with a license agreement if the package is not covered under the GNU General Public license.  If you install something from elsewhere, you will most likely be presented with a license agreement if such is required.

Install from the Canonical repos without worry.

If you wish, you may review the [GNU General Public License Version 2]("https://opensource.org/licenses/GPL-2.0") and the [GNU General Public License version 3]("https://opensource.org/licenses/GPL-3.0").  You may assume everything is copyrighted by someone -- which means that you may not copy and use the source code without attribution or claim it as your own work.  Unless you are a software developer, this is not likely to affect you.

You may freely install and use any package you find in the repos.  If you install from the Ubuntu Software Center, or whatever they are calling it these days, some packages may require the payment of a purchase fee for use, but you will be advised of that.

---

### Post by Holger_Gehrke on 2018-06-22
The most common licenses used by Free and Open Source Software can be found on an Ubuntu system in the directory '/usr/share/common-licenses'.

You mistyped the command I gave you in my last post: 'dpkg -S $**(which** ifconfig**)**'. The '$(  )' means execute the command inside the parentheses and replace it in the command line with its output. 'which' is a command to find the full path for a program file 'dpkg -s' or 'dpkg --show' expect a full path to search for the package a file is part of. Of course this only works for programs that are already installed.

If you absolutely positively need to know the license in advance of  installing a piece of software, you need to find the homepage of the  author or project that created it and look there. If you know the package for a program you want to install but haven't yet, you can use 'apt show packagename'. Among the information this shows you can find the homepage for the program which should give you a way to find out under what license the program is available. Programs and packages are not necessarily the same thing. Some big programs are split into several packages (vlc for example is made up of 20 packages, not all of which are needed; to make matters more complicated: some of these packages may contain plugins for vlc by authors not associated with videolan.org which may be under a different license from the main program), some separate but related small programs are one package (net-tools contains not only ifconfig but also netstat, ipmaddr, iptunnel, mii-tool, nameif, plipconfig, rarp, route, slattach, and arp).

But unless you're involved in the kind of situation HermanAB mentioned, QIII is completely right. For end-users the various open source licenses are close to the same and the software in the repositories (with the exceptions already mentioned) is all licensed under one of them.

Holger

---

### Post by ghegheg on 2018-06-23
I understand, the licences is free or GPL if I install from Canonical main repo or Canonical universe repos (this last case, I will be adviced if exist a purchase fee). 

Because I still learn after a book, it is unclear to me: the command "apt get install yyy-program" install yyy-program from main repo and universe repo?

---

### Post by deadflowr on 2018-06-23
> Because I still learn after a book, it is unclear to me: the command "apt get install yyy-program" install yyy-program from main repo and universe repo?
Since apt handles dependency issues, a package you install might download from both.
A package you want might require dependencies from the other repository.
you can use 
```
apt policy package-name-here
or
apt-cache policy package-name-here
```
which will show where a package is in relation to the repository it's from.

---

### Post by ghegheg on 2018-06-23
Let me guess! 

The other repository means another deposit of programs headed by another community, like: debian, fedora, etc, or another company which have their own rules regarding their software.

The comand "apt policy package" show me if the repository is Ubuntu or another. 

For example I type "apt policy net-tools" and the console show me: 

[U]" Candidate: 1.60+git20161116.90da8a0-1ubuntu1
  Version table:
  1.60+git20161116.90da8a0-1ubuntu1 500
  500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic/main amd64 Packages" [/U]

and I ensure that this package and its dependencies belongs Ubuntu.

---


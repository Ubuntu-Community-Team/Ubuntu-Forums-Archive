---
title: "Can't install several packages"
date: 2013-09-11
forum: General Help
---

### Post by muckijeste on 2013-09-11
Hey all, I'm running Ubuntu 12.04 LTS 64-bit and having trouble installing some programs such as Skype or Wine...I have unmet package dependencies, and all of those packages have a :i386 sufix at the end..If I try installing any of those packages I get more and more dependency errors...using apt-get -f install does nothing as if everything was okay, so I found out that I maybe need to enable Multiarch using the command [COLOR=#000000][FONT=monospace]dpkg --add-architecture i386 ; [FONT=arial]However, here's what this command reports:

[/FONT][/FONT][/COLOR]user@User-ANNS:~$ dpkg --add-architecture i386
dpkg: error: unknown option --add-architecture


Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

Does anybody have an idea that could lead to a solution of the problem? Thanks
[COLOR=#000000][FONT=monospace][FONT=arial][/FONT][/FONT][/COLOR]

---

### Post by deadflowr on 2013-09-11
Where are you trying to install them from?
They are both available from the software center, though I think skype needs the partner repos enabled.

---

### Post by Bashing-om on 2013-09-11
muckijeste; Hi !

See deadflowr's last.
and:
Post the results of terminal code:
```

sudo dpkg --print-foreign-architectures

```

Looking to see if you are multi-arch enabled at this time.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-12
Hey guys, thanks for the replies.

@deadflowr

Let's stick to Wine for now. If I try to install it through the software center, I get the "Package dependencies cannot be resolved" window with the following Details:

The following packages have unmet dependencies:


wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7.1 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package


Installing wine1.5 through the terminal gets me to a wine1.6 dependency, and wine1.6 dependency gets me to a wine1.6-i386 dependency...And when I try to install wine1.6-i386, I get a whole bunch of dependency problems with all packages having a same sufix of :i386.

@Bashing-om

That command reports:

i386

Just that.

Cheers

---

### Post by Bashing-om on 2013-09-12
muckijeste; Hi !

I just installed Wine1.4 for a client on a 64 bit AMD machine ( my first) .. I did not see anything related to your output:
> 
Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed

as opposed to:
> 
 If I try to install it through the software center


I am thinking there may be a conflict due to attempting to install from 2 sources; the software-center and through PPA ???
Let's see if you also have the Wine PPA source listed:
```

ls -la /etc/apt/sources.list.d

```

[INDENT][INDENT]just goes to show; never can tell
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-13
Hey Bashing-om, thanks for your reply. Here's the output of the command

```
total 80drwxr-xr-x 2 root root 4096 Sep 13 11:07 .
drwxr-xr-x 6 root root 4096 Sep 13 11:07 ..
-rw-r--r-- 1 root root  136 Sep 13 11:07 alecive-antigone-precise.list
-rw-r--r-- 1 root root  136 Sep 13 11:07 alecive-antigone-precise.list.save
-rw-r--r-- 1 root root  142 Sep 13 11:07 audacity-team-daily-precise.list
-rw-r--r-- 1 root root  136 Sep 13 11:07 bumblebee-stable-precise.list
-rw-r--r-- 1 root root  136 Sep 13 11:07 bumblebee-stable-precise.list.save
-rw-r--r-- 1 root root  170 Sep 13 11:07 danielrichter2007-grub-customizer-precise.list
-rw-r--r-- 1 root root  170 Sep 13 11:07 danielrichter2007-grub-customizer-precise.list.save
-rw-r--r-- 1 root root  176 Sep 13 11:07 google-chrome.list
-rw-r--r-- 1 root root  176 Sep 13 11:07 google-chrome.list.save
-rw-r--r-- 1 root root    0 Sep 11 21:22 mefrio-g-plymouthmanager-precise.list
-rw-r--r-- 1 root root   78 Sep 11 21:22 mefrio-g-plymouthmanager-precise.list.save
-rw-r--r-- 1 root root    0 Sep 11 21:26 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root   74 Sep 11 21:26 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root    0 Sep 11 21:27 noobslab-swar-themes-precise.list
-rw-r--r-- 1 root root   74 Sep 11 21:27 noobslab-swar-themes-precise.list.save
-rw-r--r-- 1 root root  134 Sep 13 11:07 noobslab-themes-precise.list
-rw-r--r-- 1 root root  134 Sep 13 11:07 noobslab-themes-precise.list.save
-rw-r--r-- 1 root root  112 Sep 13 11:07 steam.list
-rw-r--r-- 1 root root  112 Sep 13 11:07 steam.list.save
-rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list.save

```

Any ideas? Cheers

---

### Post by Bashing-om on 2013-09-13
muckijeste;

I see nothing in that output that is disconcerting .. I am going to check a few things by comparing what was installed on the Wine install I did for my client ..

Be back soonest.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-13
We should not be limited to Wine and remember that other programs that use i386 libraries can't be installed either. What confuses me most right now is that dpkg doesn't recognize the syntax "--add-architecture" and the MultiArch wiki shows that MultiArch is enabled that way...Any ideas on that?

Cheers

---

### Post by Yellow Pasque on 2013-09-13
[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)
...
> In 12.04, the package management tools have not fully been updated to be multiarch-aware.

---

### Post by Bashing-om on 2013-09-13
muckijeste;

The command "sudo dpkg --add-architecture i386" is depreciated, and no longer valid. With the advent of "multi-arch" enabled kernels there is no longer the requirement to explicitly install "ia32-libs".

Ok, per the output of "dpkg --print-foreign-architectures" you are 32 bit enabled. Thus we are back to looking at the source of the dependency issues. And yeah, the problem may indeed be  specific to Wine - looked at that install I did and was pleasantly surprised at what I did not find. Wine has come a long way since I was first aware of it.

however, that fresh install of Wine1.4 from the software ceneter DOES NOT enable additional repository in /etc/apt/sources.list.d directory.
Yours:
> 
rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list.save


Let's see if we can get rid of it - don't know for sure that this will,  but try::
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:1.4.1-0ubuntu1~precise1~ppa4

```

Depending on how the above goes, may have to also;
(un-)install Wine that was installed from USC .. and then try and install Wine once more from the software-center.


[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2013-09-13
> **Bashing-om said:**
> The command "sudo dpkg --add-architecture i386" is deprecated, and no longer valid. With the advent of "multi-arch" enabled kernels there is no longer the requirement to explicitly install "ia32-libs".

You've got it backwards.. "--add-architecture" is not deprecated and is used for multiarch in Ubuntu 12.10 and later. Read the link in my last post. Ubuntu 12.04 is kind of odd in how it handles multiarch because it's stuck between the old and the new multiarch schemes.

---

### Post by Bashing-om on 2013-09-13
@ Temüjin. Thank you for the clarification, I do stand corrected. The follow up link is also interesting:
[https://wiki.debian.org/Multiarch/](https://wiki.debian.org/Multiarch/)

@ muckijeste; fact remains, we need to remove the Wine install done via the PPA.

[INDENT][INDENT]it is all a process of learning[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-14
Hey Bashing-om,

Not sure if I'm quite following. Remove the Wine install done via the PPA? There was no wine install done via the PPA, I only added the PPA to the APT but couldn't install it at all because it was having dependency problems. Thus the ppa purge command you gave me reports this:

```

l33t@1337-ANNS:~$ sudo ppa-purge ppa:1.4.1-0ubuntu1~precise1~ppa4
Updating packages lists
PPA to be removed: ppa:1.4.1-0ubuntu1~precise1~ppa4 
ppa:1.4.1-0ubuntu1~precise1~ppa4
Warning:  Could not find package list for PPA: ppa:1.4.1-0ubuntu1~precise1~ppa4 
ppa:1.4.1-0ubuntu1~precise1~ppa4

```

Anything on that?

Cheers

---

### Post by Bashing-om on 2013-09-14
muckijeste; Hey;
I am far from an expert on "wine", nor do I claim to have a lot of knowledge in that respect.
this from your system:
> 
-rw-r--r-- 1 root root  112 Sep 13 11:07 steam.list
-rw-r--r-- 1 root root  112 Sep 13 11:07 steam.list.save
-rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root  134 Sep 13 11:07 ubuntu-wine-ppa-precise.list.save
 in my limited experience tells me that an install was attempted from a ppa .. and I could be totally in error,
The fact remains that there exist dependency issues .. generally caused by trying to install 2 versions of the same program.
In your case I see both amd64 as well as i386 -> differing architectures and versions !
> 
Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa4) but 1.4.1-0ubuntu1~precise1~ppa4 is to be installed
Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa4) but it is a virtual package

In preparation to dealing with Wine, let's clear the background;
Before we get all hot and bothered, lets try and isolate for sure where the problem lies. Let's turn off all the PPAs temporarily and run the update routine once more to see what then the package manager has to relate.

In software sources - other software - uncheck all of the PPA's and then in terminal run:
```

sudo apt-get update
sudo apt-get upgrade

```
It that runs with no errors, turn on the PPAs .. one at a time and at each run the update routine. When the package manager screams and hollers we will have a great indication of where the fault lies !
If the PM is unhappy even at the first instance, best look at the source.list file. See what is enabled there.

[INDENT]my thoughts on a troubleshooting technique 
[/INDENT]

---

### Post by muckijeste on 2013-09-14
Hey Bashing-om

Thanks for your replies and effort to help but I think this isn't getting us anywhere. The update and upgrade commands run without any errors even when all of the PPAs are enabled in Software Sources. This is really bugging me out...

---

### Post by Bashing-om on 2013-09-14
muckijeste; All well and good.

I advocate the complete removal of Wine and then try and re-install. we can do this .. prior to starting make a backup of the list of all files installed .. such that we can make sure all traces have been removed using that file as a guide.

If you choose to continue:
show the output of:
```

ls -l /var/lib/dpkg/info/wine*

```
and copy those files to someplace safe with a different name .. as to the desktop and a name such as "remove.txt".

[INDENT][INDENT]dependencies must be resolved
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-15
Bashing-om; As I said, I'm not sure what you are trying to do. If I got everything good, you think that I have a corrupted wine installation on my computer and now you want me to remove it so I can install wine correctly? If that's the case, no, I don't have a single wine file installed on my computer.

Here's the output of the command:
```

ls: cannot access /var/lib/dpkg/info/wine*: No such file or directory

```

As I said, I'm a complete linux noob, but this problem is related to all programs using the i386 32-bit architecture. But since I'm a complete noob and (most likely) don't know what I am talking about, I will do anything you say to solve the problem because it's really screwing me up...I have a lot of 32-bit programs I want to run and I can't find a reason why I can't.

Cheers

---

### Post by Bashing-om on 2013-09-15
muckijeste; Good morning.

I am presently booted into version 12.04, running kernel 3.2.0-53-generic. 
1. I can confirm that the command "dpkg --add-architecture i386" is indeed not valid.
2. I can confirm that installing Wine1.4 on 13.04, from synaptic - software center, your ppa:
> 
-rw-r--r-- 1 root root 134 Sep 13 11:07 ubuntu-wine-ppa-precise.list
-rw-r--r-- 1 root root 134 Sep 13 11:07 ubuntu-wine-ppa-precise.list.save 

was not part of that install process.
3. ubuntu's package manager is very smart, but, it does not always know what our intentions are and will tell us -as in this case- that it can not comply with what it is directed to do. Then as it can not comply, it will give us hints on the why and whereall. Now the package manager is directing our attention to Wine, advising there are conflicts. I am heeding it's advise and in order to straighten up the system I want to remove that possible conflict. The way I know to do so is to remove Wine entirely such that then there are no conflicts. I would much much prefer to do this removal through the package management system rather than having to do this manually, entailing having to hunt up each and every file related to wine and manually removing those files. Then if you want Wine on your system .. install it properly through ubuntu's package manager.
4. To that end of installing a 32bit application on 64 bit hardware .. we need to insure that the 32bit libraries are installable.
Post back the results:
```

cat /etc/dpkg/dpkg.cfg.d/multiarch
sudo apt-cache policy ia32-libs

```
We know that your system is 32bit enabled by the output from: "dpkg --print-foreign-architectures ".

5. Now as said I prefer the option to let the package manager do our tedious work of removal for us, I still want to explore a means of "ppa-purge" to remove that PPA install. I may not have the proper version in that last attempt and I want to see at this time how the system is fetching the Wine PPA.
```

cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list

```
If that method is unproductive, my next is to try removal of wine with " apt-get remove --purge" commands. Upon completion, insure the job was done right by consulting what should have been in the "/var/lib/dpkg/info/<package_name.list> file.
For you reference do:
```

ls -la /var/lib/dpkg/info/gedit*

```
When all else fails in this attempt to remove Wine and to get the system stable.. then will resort to manually hunting up files and removing them from the system... not a prospect to anticipate!

Be aware, in a situation such as this .. there is no easy answer. One way or another, whatever the underling cause, those dependencies must be satisfied !

OK, what do you want to do ?

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-15
Evening here, Bashing-om :D

You have confused me even more now, it's best for me to stick to doing what you say than getting into all those complex things. Thanks for giving an explanation though.

As for our problem here, I will present you the outputs of all the commands you gave me, and I'll leave you the choice what to do next.

```

l33t@1337-ANNS:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
foreign-architecture i386
l33t@1337-ANNS:~$ sudo apt-cache policy ia32-libs
[sudo] password for l33t: 
ia32-libs:
  Installed: (none)
  Candidate: 20090808ubuntu36
  Version table:
     20090808ubuntu36 0
        500 http://rs.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
     20090808ubuntu35 0
        500 http://rs.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

```

l33t@1337-ANNS:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

```

```

l33t@1337-ANNS:~$ ls -la /var/lib/dpkg/info/gedit*
-rw-r--r-- 1 root root 101388 Aug 20 19:58 /var/lib/dpkg/info/gedit-common.list
-rw-r--r-- 1 root root   9512 Apr 16  2012 /var/lib/dpkg/info/gedit-common.md5sums
-rw-r--r-- 1 root root   3724 Aug 20 19:58 /var/lib/dpkg/info/gedit.list
-rw-r--r-- 1 root root   5224 Apr 16  2012 /var/lib/dpkg/info/gedit.md5sums
-rwxr-xr-x 1 root root   1325 Apr 16  2012 /var/lib/dpkg/info/gedit.postinst
-rwxr-xr-x 1 root root    275 Apr 16  2012 /var/lib/dpkg/info/gedit.postrm
-rwxr-xr-x 1 root root    582 Apr 16  2012 /var/lib/dpkg/info/gedit.prerm
-rw-r--r-- 1 root root     25 Apr 16  2012 /var/lib/dpkg/info/gedit.shlibs

```

I think we're getting onto something here. Not exactly sure what though. Do these outputs help you think of a solution?

Cheers

---

### Post by Bashing-om on 2013-09-15
muckijeste; That's the spirit !

Ok here is what we now know:
Your system is 32bit enabled,
Your system DOES not have the 32bit libs installed - will fix that when Wine is purged,
Your system has dependency problems and the package manager points us to Wine,
Your system only has Wine partially installed (/var/lib/dpkg/info/wine* tells us that),
We are going to remove all traces of wine, and start afresh.

To removal .. we want to know what we are dealing with; Before we jump further in (just in case).
Show me:
```

sudo dpkg --list | grep wine
apt-cache policy wine

```
Then I will be better prepared to remove the Wine PPA and all instances of wine.
I will try the package management systems tools first !

[INDENT][INDENT]let's get wet all over
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-16
Hey there Bashing-om,

just a question here out of curiosity; how comes in your last post you've made me do a "ls -la" command with the "gedit" query? What does the text editor have to do with wine?

As for the commands in the current post, here is the output:

```

l33t@1337-ANNS:~$ sudo dpkg --list | grep wine
l33t@1337-ANNS:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.7.1-actually1.6-0ubuntu1
  Version table:
     1.7.1-actually1.6-0ubuntu1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
     1.4-0ubuntu4.1 0
        500 http://rs.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
     1.4-0ubuntu4 0
        500 http://rs.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

Does that mean anything to you?

Cheers

---

### Post by Bashing-om on 2013-09-16
muckijeste; Hey.

The ls command in respect to "gedit" was only to demonstrate to you the validity of the command to look at the "list" for "wine" entries. I want you comfortable with what we are doing and as well to have confidence in what I direct you to do. Always, always ask questions for anything not understood !

With that output we can rest assured that "Wine" is not fully installed. Thus not to be upset when a removal command does not respond.
Now I am going to try and remove that PPA install of wine, we know it is not installed completely and ppa-purge will in all likely hood fail. But. I want to give the package manager a chance to deal with the situation -as best it can - and as well see if/what errors are generated. And yes, we have been here before for this step in the procedure. I prefer in this instance to do it in baby steps.
To that end let us start at the beginning and do:
```

sudo ppa-purge ppa:ubuntu-wine/ppa

```Note the change in the command's argument from the former specific argument - as related by:
> 
l33t@1337-ANNS:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) precise main

Next is to remove that source list .. first I want to see what ppa-purge relates to us.

We are doing baby steps to get your system 32bit enabled !

[INDENT][INDENT][INDENT]it is all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-16
Thanks for the explanation Bashing-om.

PPA purged successfully. When executed, the command

```

apt-cache policy wine

```

now shows only the packages from the official repositories. Is that what we were looking for? If yes, what's the next baby step? :D

---

### Post by Bashing-om on 2013-09-16
muckijeste; Regret the delay in getting back.
Ok !
As we are done now with the PPA .. remove the related source list:
```

sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
sudo rm /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list.save

```
do in terminal -for later reference -:
```

sudo dpkg --list | grep wine

```
And now to get rid of the partial install of wine from the software center:
```

sudo apt-get --purge remove wine

``` be advised there is in all likely hood not enough installed for "apt-get" to work with.
If so, will have to resort to the hunt peck system and remove files manually

And now is a good time to look at your source.list file and make sure all is in shape:
```

cat /etc/apt/sources.list

```

[INDENT][INDENT]small steps but great progress
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-17
Hey Bashing-om,

The rm command did it's work.

The dpkg --list command didn't show up anything.

The apt-get --purge remove command said that the package "wine" is not installed and thus can't be removed.

The cat command outputs this:
```

l33t@1337-ANNS:~$ cat /etc/apt/sources.list
deb http://rs.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://rs.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://rs.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise universe
deb http://rs.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://rs.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://rs.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://rs.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://rs.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

I suppose we're going to have to remove the wine files manually?

Cheers

---

### Post by Bashing-om on 2013-09-17
muckijeste; Well // All looking good at this point .. now lets see about having to manually attack things .. this command will tell the tale:
show the output of:
```

find / -name "wine*"

```
just look'n, that "*" character will match up whatever .. and what it matches may have nothing to do with the Wine install .. look carefully (me) before proceeding ...
Hopefully though we are done with this step and can move on to getting the 32bit library situation under our control.

I am done in for the time being .. I will check back in asap tomorrow.

[INDENT][INDENT]getting there is half the fun
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-17
```

/media/0EE8AE86E8AE6C21/Windows/System32/en-US/winethc.dll.mui
/media/0EE8AE86E8AE6C21/Windows/System32/winethc.dll
/media/0EE8AE86E8AE6C21/Windows/System32/winevt
/media/0EE8AE86E8AE6C21/Windows/winsxs/amd64_microsoft-windows-w..lperclass.resources_31bf3856ad364e35_6.1.7600.16385_en-us_43e9d5eaf537a5d6/winethc.dll.mui
/media/0EE8AE86E8AE6C21/Windows/winsxs/amd64_microsoft-windows-wininethelperclass_31bf3856ad364e35_6.1.7600.16385_none_8124dc1852de3883/winethc.dll
/media/0EE8AE86E8AE6C21/Games/Counter-Strike/cstrike/models/winebottle.mdl
/media/0EE8AE86E8AE6C21/Games/Counter-Strike/cstrike/sound/radio/bot/wine_cellar.wav
/usr/share/app-install/icons/wine.png
/usr/share/app-install/icons/wine-winetricks.png
/usr/share/app-install/desktop/wine1.4:wine.desktop
/usr/share/app-install/desktop/winetricks:wine-winetricks.desktop
/usr/share/app-install/desktop/winefish:winefish.desktop
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine-uninstaller.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine-winecfg.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine-notepad.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/winegame.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine_doors.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine.png
/usr/share/icons/AwOkenDark/clear/24x24/apps/wine-winetricks.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine-uninstaller.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine-winecfg.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine-notepad.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/winegame.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine_doors.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine.png
/usr/share/icons/AwOkenDark/clear/128x128/apps/wine-winetricks.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine-uninstaller.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine-winecfg.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine-notepad.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/winegame.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine_doors.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine.png
/usr/share/icons/AwOkenWhite/clear/24x24/apps/wine-winetricks.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine-uninstaller.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine-winecfg.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine-notepad.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/winegame.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine_doors.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine.png
/usr/share/icons/AwOkenWhite/clear/128x128/apps/wine-winetricks.png
/usr/share/icons/AwOken/clear/24x24/apps/wine-uninstaller.png
/usr/share/icons/AwOken/clear/24x24/apps/wine-winecfg.png
/usr/share/icons/AwOken/clear/24x24/apps/wine-notepad.png
/usr/share/icons/AwOken/clear/24x24/apps/winegame.png
/usr/share/icons/AwOken/clear/24x24/apps/wine_doors.png
/usr/share/icons/AwOken/clear/24x24/apps/wine.png
/usr/share/icons/AwOken/clear/24x24/apps/wine-winetricks.png
/usr/share/icons/AwOken/clear/128x128/apps/wine-uninstaller.png
/usr/share/icons/AwOken/clear/128x128/apps/wine-winecfg.png
/usr/share/icons/AwOken/clear/128x128/apps/wine-notepad.png
/usr/share/icons/AwOken/clear/128x128/apps/winegame.png
/usr/share/icons/AwOken/clear/128x128/apps/wine_doors.png
/usr/share/icons/AwOken/clear/128x128/apps/wine.png
/usr/share/icons/AwOken/clear/128x128/apps/wine-winetricks.png

```

These ones are catching to my eyes the most:

```

/usr/share/app-install/icons/wine.png
/usr/share/app-install/icons/wine-winetricks.png
/usr/share/app-install/desktop/wine1.4:wine.desktop
/usr/share/app-install/desktop/winetricks:wine-winetricks.desktop
/usr/share/app-install/desktop/winefish:winefish.desktop

```

Do you agree? What's the next baby step?

Cheers

---

### Post by Bashing-om on 2013-09-17
muckijeste; Hi !

IF you intend to (re)install Wine, I think we can safely disregard the files I see in that one out put. We will overwrite them in the install.
I do want to make double sure that the executable file is gone, just for saftys' sake and peace of my mind, let's look.
```

ls -la /usr/bin/wine

```
A return of "No such file or directory" is a good thing.
Next steps  depend on if you want to install 32 bit applications. Many 3rd party aps are only available in a 32 bit version.
Steam, I bet for sure, requires 32 bit libraries.

[INDENT]small steps, getting there
[/INDENT]

---

### Post by muckijeste on 2013-09-17
Hey Bashing-om!

Yes, the output is "No such file or directory" :)

And yes, I want to install 32-bit applications, but I couldn't, that's why I opened this topic. So what next?

---

### Post by Bashing-om on 2013-09-17
muckijeste; Hey !

I anticipate we are home free ..
Let's have the package manager check it's dependencies:
```

sudo apt-get install -f

```
and per launchpad:
> 
Steve Langasek (vorlon) wrote on 2012-06-07:
Note that you generally should *not* need ia32-libs nowadays; you should be able to just install the i386 version of whatever package you need. ia32-libs is present in 12.04 for upgrade compatibility only.


If there exist no issues from "sudo apt-get install -f" then let's install Wine and see what happens:
```

sudo apt-get install wine

```
[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-17
No issues during "sudo apt-get install -f".

```

l33t@1337-ANNS:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gvfs-daemons : Depends: x11-utils
 wine : Depends: wine1.4 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

```

l33t@1337-ANNS:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.14.0-0ubuntu6)
        Depends: gvfs-daemons (< 1.14.0-0ubuntu6.1~)
 wine1.4 : Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but it is not going to be installed
           Depends: wine1.4-i386 (= 1.4.1-0ubuntu1)
           Recommends: winetricks but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

Installing wine1.4-amd64 gets me to a wine1.4-common dependency, and wine1.4-common dependency gets me back to the wine1.4 dependency. Installing wine1.4-i386 gets me to this:

```

l33t@1337-ANNS:~$ sudo apt-get install wine1.4-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.14.0-0ubuntu6)
        Depends: gvfs-daemons (< 1.14.0-0ubuntu6.1~)
 wine1.4-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Depends: wine1.4-common:i386 (= 1.4.1-0ubuntu1)
                     Recommends: gettext:i386 but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

I think I'm pretty much stuck from here on. What do you suggest?

---

### Post by Bashing-om on 2013-09-17
muckijeste; Well, could be a lot worse !

At least there is no screaming and hollering about the ia32libs or ia32-libs-multiarch.

Let's try a shortcut and see if this helps... else: we will descend the dependency trail.
try:
```

sudo apt-get build-dep wine

```
[INDENT][INDENT]if at first you do not succeed (sky diving excepted)[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-17
Hey Bashing-om,

here's the output:
```

l33t@1337-ANNS:~$ sudo apt-get build-dep wine
[sudo] password for l33t: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'wine1.4' as source package instead of 'wine'
The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 9.0.3-0ubuntu0.2) but it is not going to be installed
                   Depends: libdrm-dev (>= 2.4.24) but it is not going to be installed
E: Build-dependencies for wine could not be satisfied.

```

Ideas?

Cheers

---

### Post by Bashing-om on 2013-09-18
muckijeste; Disappointing ..but oh well !

We will start looking at the dependencies and getting down to the bottom .. install our way back up ..

It is my witching hour now, my thinking is cloudy so will commence soonest in my Am. I will start building a flow chart.

I will advise soonest I can.

[INDENT][INDENT]cheers till
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-18
Sure thing mate, thanks for your help so far.

---

### Post by Bashing-om on 2013-09-18
muckijeste; Hi !

Ok .. let's see if we can get down to the bottom of all this.
First do some light house cleaning .. just to preclude any other interference with our hunting.
In terminal do:
The "#" character means a comment and is not to be executed !
```

#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a #All that does is update it again.

```
When all that runs clean .. start this tedious process for resolving dependencies ... several chains will be developed.

Here is the start of these chains: show me:
```

apt-get install wine1.4-common:i386
apt-get install libgl1:i386
apt-get install libglu1:i386

```looks as good as any place to start as I do not see any deep dependency issues with the 2 libraries.
Then we will roll  our sleeves up and really go to work !

[INDENT][INDENT]an intriguing little puzzle 
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-18
Hey there Bashing-om.

The clean up commands did a lot of work. However, the dependency issues are still here:

```

l33t@1337-ANNS:~$ sudo apt-get install wine1.4-common:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'wine1.4-common' instead of 'wine1.4-common:i386'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gvfs-daemons : Depends: x11-utils
 wine1.4-common : Depends: wine1.4 (= 1.4.1-0ubuntu1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

```

l33t@1337-ANNS:~$ sudo apt-get install libgl1:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libgl1-mesa-glx:i386' instead of 'libgl1:i386'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gvfs : Depends: gvfs-daemons (>= 1.14.0-0ubuntu6)
        Depends: gvfs-daemons (< 1.14.0-0ubuntu6.1~)
 libgl1-mesa-glx:i386 : Depends: libdrm2:i386 (>= 2.3.1) but it is not going to be installed
                        Recommends: libgl1-mesa-dri:i386 (>= 7.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

```

l33t@1337-ANNS:~$ sudo apt-get install libglu1:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libglu1-mesa:i386' instead of 'libglu1:i386'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libglu1-mesa:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
E: Unable to correct problems, you have held broken packages.

```



Any more ideas?

Cheers

---

### Post by Bashing-om on 2013-09-18
muckijeste; Here goes ..
All that housecleaning would have no direct effect on our issue, just to insure the base was clean. 
my flowchart updated with the info,, descending lower ..
show the results:
```

sudo apt-get install x11-utils
sudo apt-get install libgl1-mesa-glx:i386
sudo apt-get install libdrm2:i386

```
Yeah a bit redundant, but I do want to see what the package manager says. "x11-utils" seems to be the biggy.
Be aware, this is going to be a long tedious process - the reason for the flow charting -..communications lag is going to make it longer ...
We are currently only working one chain .. I am presently aware of 3 other chains to be resolved. I can fully understand if you get impatient .. and need to have your system fully functional quick .. and you then decide the thing to do is (RE-)install... and start from that clean install to install the 32bit applications.

[INDENT][INDENT]work'n to get to the bottom
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
Hey mate,

I think I have some important information that could lead to ideas for a solution. Yesterday I have successfully upgraded my Ubuntu to 12.10 and have just found out that when I go to "Software Sources", none of the official repositories are actually enabled. With all of them disabled, when "sudo apt-get update" is ran, I get a big list with around 750kB of data fetched during the update. However, when I ENABLE all of the official repositories in Software Sources, when "sudo apt-get update" is ran, I get just a few entries for the multiverse repository with the total of 25kB of data fetched. This was very confusing, however, I tried reinstalling "libgl1:i386" and "libglu1:i386" with all the repositories ENABLED, and the package manager reported that those packages have been replaced by "libgl1-mesa-glx" and "libglu1-mesa". I thought the i386 dependency issues were finally resolved, but when I tried installing wine, it said it couldn't find the package "wine". I then tried adding the wine repository again and installing wine from it, but I got a big number of i386 packages issues again, so I just purged the wine repository again.

What's confusing me the most is that when the official repositories are DISABLED, I get a load of entries when "sudo apt-get update" is ran, and I also get dependency issues with the packages required for wine. However, when the official repositories are ENABLED, I get barely a few entries with "sudo apt-get update" and there are no more dependency issues with the packages required for wine, however, wine is not found anymore. It would be more logical if it was vice versa, right?

I smell this has something to do with my 12.04 to 12.10 update.

Anyway, where should we continue from? With the official repositories enabled or disabled?

Cheers

---

### Post by Bashing-om on 2013-09-19
muckijeste; mYuk !

off topic: Hey I rearranged my schedule this morning to meet ya sooner .. and some how I still missed your update !

On Topic: Yeah I agree. there must be a rat in the wood pile, I too can not make sense of the reverse logic on repos enabled/disabled.
Not finding Wine I can understand if the repos were disabled;
And I was aware of the "libgl1-mesa-glx" placement ( from your prior outputs ).

I would have expected upgrading to 12.10 to have resolved all those dependencies ! ... If the ubuntu repositories were all enabled ... and we are not talking about PPAs ...from the command line:
```

sudo apt-get install wine

```
should have done it's magic // should have been done and over with at that point. I have not a clue why not.
That said, if it were me in this situation ... I would:
back up my data,
wipe that disk clean (GParted),
install from scratch 12.04.XX (depending on driver support for my graphics card the version I would install),
insure all ubuntu repositories are enabled,
THEN:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine

```
I firmly endorse installing wine from the official repository, so what if what is available in the repo is a version behind what may be obtained from the PPA . That is where you are getting those dependency issues !
As one installs only from the official repository .. one remains under the "umbrella" of protection - the package manager can and will do it's job, keeping you safe and stable. And yes that is at the expense of having "the latest version",
Stability of the primary operating system is always preferred.

Final comment /// best solution now is (RE-)install. However, I am here to help, in what ever means you require but, I do not foresee within version 12.10 dependency resolvement to be either easy or straight forward .. really going to be hunting down those dependency issues maybe on several fronts ?  
[INDENT][INDENT]what ever you want to do
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
That seems very reasonable Bashing-om.

Well, I guess I'll be looking at a fresh installed Ubuntu 12.04 then :)

Thanks for all your effort and help, it is really appreciated.

Cheers :)

---

### Post by Bashing-om on 2013-09-19
muckijeste; Hey !
Not a problem .. open source - ubuntu ! - we are all in this together.

I really think that the better course is to (re)install  .. and from a wiped disk .. makes sure none of the configurations gets transpired into that new install .. You want a clean slate at this point.
Do not mix repositories/PPA's ! The package manager wants all within it's own index files, else it can and does loose track of what it is doing.

My best to ya.
[INDENT][INDENT]holler at us if ya need additional assist
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
Hey Bashing-om...

This is making me nervous and angry...I have formatted my Ubuntu partition and reinstalled Ubuntu 12.04...But the dependency problems are there! I haven't added any custom repos so this is all from the official ones. The dependency issues are a bit different than on the old Ubuntu. Check this out:

```

l33t@l33t-X55VD:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
l33t@l33t-X55VD:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1)
E: Unable to correct problems, you have held broken packages.
l33t@l33t-X55VD:~$ sudo apt-get install wine1.4-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4-i386:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not going to be installed
                     Depends: libc6:i386 (>= 2.9) but it is not going to be installed
                     Depends: libgl1-mesa-glx:i386 or
                              libgl1:i386
                     Depends: libglib2.0-0:i386 (>= 2.16.0) but it is not going to be installed
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Depends: libgphoto2-2:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port0:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgstreamer-plugins-base0.10-0:i386 (>= 0.10.22) but it is not going to be installed
                     Depends: libgstreamer0.10-0:i386 (>= 0.10.26) but it is not going to be installed
                     Depends: liblcms1:i386 (>= 1.15-1) but it is not going to be installed
                     Depends: libldap-2.4-2:i386 (>= 2.4.7) but it is not going to be installed
                     Depends: libmpg123-0:i386 (>= 1.6.2) but it is not going to be installed
                     Depends: libopenal1:i386 (>= 1:1.13) but it is not going to be installed
                     Depends: libsm6:i386 but it is not going to be installed
                     Depends: libx11-6:i386 but it is not going to be installed
                     Depends: libxext6:i386 but it is not going to be installed
                     Depends: libxml2:i386 (>= 2.7.4) but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Depends: libncurses5:i386 but it is not going to be installed
                     Recommends: gettext:i386 but it is not going to be installed
                     Recommends: libcapi20-3:i386 but it is not going to be installed
                     Recommends: libcups2:i386 but it is not going to be installed
                     Recommends: libdbus-1-3:i386 but it is not going to be installed
                     Recommends: libfontconfig1:i386 but it is not going to be installed or
                                 libfontconfig:i386
                     Recommends: libfreetype6:i386 but it is not going to be installed
                     Recommends: libgif4:i386 but it is not going to be installed
                     Recommends: libgnutls26:i386 but it is not going to be installed
                     Recommends: libjpeg8:i386 but it is not going to be installed
                     Recommends: libpng12-0:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
                     Recommends: libssl1.0.0:i386 but it is not going to be installed
                     Recommends: libtiff4:i386 but it is not going to be installed
                     Recommends: libv4l-0:i386 but it is not going to be installed
                     Recommends: libxcomposite1:i386 but it is not going to be installed
                     Recommends: libxcursor1:i386 but it is not going to be installed
                     Recommends: libxi6:i386 but it is not going to be installed
                     Recommends: libxinerama1:i386 but it is not going to be installed
                     Recommends: libxrandr2:i386 but it is not going to be installed
                     Recommends: libxrender1:i386 but it is not going to be installed
                     Recommends: libxslt1.1:i386 but it is not going to be installed
                     Recommends: libxt6:i386 but it is not going to be installed
                     Recommends: libxxf86vm1:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Does this mean anything to you? Any ideas?

Cheers

---

### Post by Bashing-om on 2013-09-19
muckijeste;

Just a quick look at it .. seems that multiarch did not install, and yeah it is supposed to ! - Let's look,
```

dpkg --print-architecture
dpkg --print-foreign-architectures
cat /etc/dpkg/dpkg.cfg.d/multiarch
cat /var/lib/dpkg/arch
dpkg -l ia32-libs-multiarch

```
Now, did you run the update routine prior to trying to install Wine ?
What specific version of 12.04 are you installing .. 12.04.1 and others do have different kernels .. maybe the earlier kernel is not too multiarch compliant ?

We certainly need to get to find the reason !
[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
Hey Bash,

Yes, I've run the update routine. I think I'm running Ubuntu 12.04.3 with the newest 3.8.0-30 kernel, that's how it displays in the GRUB. And looks like you're right, multiarch seems to be only partially installed. Take a look:

```

l33t@l33t-X55VD:~$ dpkg --print-architecture
amd64
l33t@l33t-X55VD:~$ dpkg --print-foreign-architectures
i386
l33t@l33t-X55VD:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
foreign-architecture i386
l33t@l33t-X55VD:~$ cat /var/lib/dpkg/arch
cat: /var/lib/dpkg/arch: No such file or directory
l33t@l33t-X55VD:~$ dpkg -l ia32-libs-multiarch
No packages found matching ia32-libs-multiarch.

```

Cheers

---

### Post by Bashing-om on 2013-09-19
muckijeste; Yuk. Yep, and that is contray to everything that is documented .. what to do what to so ?

let's check one other thing:
> 
multiarch support is present from dpkg 1.16.2 (or 1.16.0 in Ubuntu) and apt 0.8.13.

so let's see:
```

dpkg -l dpkg
dpkg -l apt

```

Dotting i's and crossing t's ::
formatted the ubuntu partition(s) .. check
fresh install of ubuntu version 12.04.3 ...check
verified that ALL repositories in the ubuntu software system is enabled within USC -> software sources ...check(don't care about "src" code)
ran the sudo update/upgrade routine .. check
terminal code "sudo apt-get install wine"... check

And still multiarch did not happen ?

[INDENT][INDENT]now, it is indeed a puzzle
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
All seems good here:
```

l33t@l33t-X55VD:~$ dpkg -l dpkg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  dpkg           1.16.1.2ubuntu Debian package management system
l33t@l33t-X55VD:~$ dpkg -l apt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  apt            0.8.16~exp12ub commandline package manager


```

Aaaand....voila! I have changed the repo download server in the Software Sources from "Server for Serbia" to "Main Server"; ran the update command which now fetched 27MB of data; ran the upgrade command which updated a lot of packages (though most of them seem irrelevant to our problem, but doesn't matter anyway)...ran "sudo apt-get install wine"...

```

l33t@l33t-X55VD:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  efibootmgr secureboot-db thunderbird-globalmenu
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core
  gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386
  libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libencode-locale-perl
  libexif12:i386 libexpat1:i386 libffi6:i386 libfile-listing-perl
  libfont-afm-perl libfontconfig1:i386 libfreetype6:i386 libgcc1:i386
  libgcrypt11:i386 libgd2-xpm:i386 libgettextpo0 libgif4 libgif4:i386
  libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring:i386
  libglapi-mesa-lts-raring:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgpm2:i386 libgraph4 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386
  libldap-2.4-2:i386 libllvm3.2:i386 liblqr-1-0 libltdl7:i386
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore4
  libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libodbc1 libopenal1:i386 libopenexr6 liborc-0.4-0:i386
  libp11-kit0:i386 libpam-winbind libpathplan4 libpciaccess0:i386
  libpcre3:i386 libpng12-0:i386 libroken18-heimdal:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386 libsm6:i386
  libsocket6-perl libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-3:i386 libtiff4:i386 libtimedate-perl libtinfo5:i386
  libtxc-dxtn-s2tc0:i386 libunistring0 liburi-perl libusb-0.1-4:i386
  libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libwind0-heimdal:i386
  libwww-perl libwww-robotrules-perl libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386
  libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2 ttf-droid
  ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar
  winbind wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386 winetricks zlib1g:i386
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl imagemagick-doc
  autotrace curl enscript ffmpeg gimp gnuplot grads hp2xx html2ps libwmf-bin
  mplayer povray radiance texlive-base-bin transfig ufraw-batch
  libasound2-plugins:i386 libasound2-python:i386 glibc-doc:i386 locales:i386
  cups-common:i386 rng-tools:i386 libgd-tools:i386 libglide3:i386
  gnutls-bin:i386 gphoto2:i386 gtkam:i386 gpm:i386 krb5-doc:i386
  krb5-user:i386 libvisual-0.4-plugins:i386 gstreamer-codec-install:i386
  gnome-codec-install:i386 gstreamer0.10-tools:i386
  gstreamer0.10-plugins-base:i386 libdata-dump-perl liblcms-utils:i386
  libcrypt-ssleay-perl libmyodbc odbc-postgresql tdsodbc unixodbc-bin
  hpoj:i386 hplip:i386 libsane-extras:i386 sane-utils:i386
  libsasl2-modules-otp:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-sql:i386 libsasl2-modules-gssapi-mit:i386
  libsasl2-modules-gssapi-heimdal:i386 libauthen-ntlm-perl dosbox
Recommended packages:
  libtxc-dxtn0:i386 xml-core:i386 gettext gettext:i386 unixodbc:i386
The following NEW packages will be installed:
  binfmt-support cabextract fonts-droid fonts-horai-umefont fonts-unfonts-core
  gcc-4.6-base:i386 gnome-exe-thumbnailer icoutils imagemagick
  imagemagick-common libasn1-8-heimdal:i386 libasound2:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386
  libc6:i386 libcapi20-3 libcapi20-3:i386 libcdt4 libcomerr2:i386
  libcups2:i386 libdb5.1:i386 libdbus-1-3:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libencode-locale-perl
  libexif12:i386 libexpat1:i386 libffi6:i386 libfile-listing-perl
  libfont-afm-perl libfontconfig1:i386 libfreetype6:i386 libgcc1:i386
  libgcrypt11:i386 libgd2-xpm:i386 libgettextpo0 libgif4 libgif4:i386
  libgl1-mesa-dri-lts-raring:i386 libgl1-mesa-glx-lts-raring:i386
  libglapi-mesa-lts-raring:i386 libglib2.0-0:i386 libglu1-mesa:i386
  libgnutls26:i386 libgpg-error0:i386 libgphoto2-2:i386 libgphoto2-port0:i386
  libgpm2:i386 libgraph4 libgssapi-krb5-2:i386 libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer0.10-0:i386 libgvc5
  libhcrypto4-heimdal:i386 libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl
  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl
  libhttp-negotiate-perl libhx509-5-heimdal:i386 libice6:i386
  libieee1284-3:i386 libilmbase6 libio-socket-inet6-perl libio-socket-ssl-perl
  libjpeg-turbo8:i386 libjpeg8:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-26-heimdal:i386 libkrb5-3:i386 libkrb5support0:i386 liblcms1:i386
  libldap-2.4-2:i386 libllvm3.2:i386 liblqr-1-0 libltdl7:i386
  liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore4
  libmagickcore4-extra libmagickwand4 libmailtools-perl libmpg123-0
  libmpg123-0:i386 libncurses5:i386 libnet-http-perl libnet-ssleay-perl
  libnetpbm10 libodbc1 libopenal1:i386 libopenexr6 liborc-0.4-0:i386
  libp11-kit0:i386 libpam-winbind libpathplan4 libpciaccess0:i386
  libpcre3:i386 libpng12-0:i386 libroken18-heimdal:i386 libsane:i386
  libsasl2-2:i386 libsasl2-modules:i386 libselinux1:i386 libsm6:i386
  libsocket6-perl libsqlite3-0:i386 libssl1.0.0:i386 libstdc++6:i386
  libtasn1-3:i386 libtiff4:i386 libtimedate-perl libtinfo5:i386
  libtxc-dxtn-s2tc0:i386 libunistring0 liburi-perl libusb-0.1-4:i386
  libuuid1:i386 libv4l-0:i386 libv4lconvert0:i386 libwind0-heimdal:i386
  libwww-perl libwww-robotrules-perl libx11-6:i386 libx11-xcb1:i386
  libxau6:i386 libxcb-dri2-0:i386 libxcb-glx0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386
  libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxml2:i386
  libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxslt1.1:i386 libxt6:i386
  libxxf86vm1:i386 netpbm odbcinst odbcinst1debian2 ttf-droid
  ttf-mscorefonts-installer ttf-umefont ttf-unfonts-core unixodbc unrar
  winbind wine wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64
  wine1.4-common wine1.4-i386:i386 winetricks zlib1g:i386
0 upgraded, 174 newly installed, 0 to remove and 0 not upgraded.
Need to get 187 MB of archives.
After this operation, 515 MB of additional disk space will be used.
Do you want to continue [Y/n]? y


```

Yes, this is a great relief! When wine has finished installing, I'll try installing some other 32-bit programs I knew didn't work...And I'll report back how it went.

Thanks Bash, you're a genius :)

BRB

Cheers

---

### Post by Bashing-om on 2013-09-19
muckijeste; Outstanding !

Nope no genius .. what I do not know fills a much larger book than the one containing what I do know !
It remains a every day process learning this operating system .. 

Changing the server mirror  .. that is something I should have thought of ! .. as I know it happens ! 

[INDENT][INDENT]all is well that ends well
[/INDENT][/INDENT]

---

### Post by muckijeste on 2013-09-19
You've got a beer from me. Or two. Three. Make that four.

Everything is working correctly, thanks for your help again, it's extremely appreciated as I was moving from Windows to Linux, and didn't want to go back to Windows just so I could run some applications that are necessary for me...

Marking as solved :)

BTW, changing the server from Serbia to Main wouldn't be effective if I haven't reinstalled Ubuntu because I've tried that on the old Ubuntu already. So both reinstalling Ubuntu and changing the server helped me get x86 enabled :)

Cheers mate

---


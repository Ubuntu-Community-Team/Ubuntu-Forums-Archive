---
title: "C compiler"
date: 2006-12-26
forum: General Help
---

### Post by rogerdrange on 2006-12-26
I'm sorry if this is the wrong place to post it, but I will try here. Feel free to move my post! :)

OK, here is the problem. Even though I've installed both gcc and build-essential, it seems like they doesn't work. When I'm trying to compiling a package, this shows up:

checking whether ln -s works... yes
checking for gcc... no
checking for cc... no


And when I'm going in apt-get and are about to install gcc, this shows up:

Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
gcc er allerede nyeste versjon.
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.


(I know, the last one is in Norwegian, but if you don't understand, it says that gcc already is installed.)


So why does apt say that it is installed, but I can't install any packages because it is not installed? ](*,) 

Please help me, and I am really sorry for my bad english! ;)

---

### Post by Sef on 2006-12-26
Have you installed build-essential?  It is necessary to install it to compile.

```
sudo aptitude update
```

```
sudo aptitude install build-essential
```

> I am really sorry for my bad english! 

Your English is fine.   No need to apologize.

---

### Post by rogerdrange on 2006-12-26
Yes, I've installed build essential.

roger@roger:~/Program/gcc-4.0.2/objdir$ sudo aptitude install build-essential
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Initializing package states ... Ferdig
Building tag database ... Ferdig      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information ... Ferdig

---

### Post by rogerdrange on 2006-12-26
What is a bit odd is that apt says that gcc is installed, but when I am about to build packages, it says that I don't have gcc..

---

### Post by zanglang on 2006-12-26
What happens if you type 'gcc' or 'cc' in a console?

---

### Post by rogerdrange on 2006-12-26
This happens, and that normally means that gcc and cc are not installed? But why dows apt say that gcc is installed then?

> roger@roger:~$ gcc
bash: gcc: command not found
roger@roger:~$ cc
bash: cc: command not found
roger@roger:~$ 


---

### Post by taurus on 2006-12-26
What does your /etc/apt/sources.list look like then?

```
cat /etc/apt/sources.list
```

---

### Post by moma on 2006-12-26
Try to reinstall the "build-essential" package.
$ [COLOR="SeaGreen"]sudo apt-get install --reinstall build-essential[/COLOR]

---

### Post by rogerdrange on 2006-12-26
> **taurus said:**
> What does your /etc/apt/sources.list look like then?

```
cat /etc/apt/sources.list
```


Here are my sources:

> roger@roger:~/Program/Uinstallert/gnome-chord2-0.7.1$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END
roger@roger:~/Program/Uinstallert/gnome-chord2-0.7.1$ 



And I have tried to reinstall build-essential, but it doesn't help. The sources.list is exactly the same as you can find at [www.ubuntuguide.org](www.ubuntuguide.org) except from the last lines, I think.

---

### Post by taurus on 2006-12-26
Insert the Edgy CD that you used to install, then at the prompt, type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitiude install build-essential
```

---

### Post by rogerdrange on 2006-12-26
> **taurus said:**
> Insert the Edgy CD that you used to install, then at the prompt, type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitiude install build-essential
```


I've tried that. I was not sure if you ment just to type it in a terminal, or to reboot the computer, and type it into the command line which appears when you choose the safe mode of starting ubuntu. But I did both, and in both cases, nothing was installed or reinstall
ed, or fixed.

](*,)

---

### Post by spockrock on 2006-12-26
try this...I use apt-get but if you use aptitude then use aptitude you should never switch between the two...... so I am gonna put apt-get but if you use aptitude then use aptitude instead of apt-get.

```
sudo apt-get remove --purge build-essential gcc 
sudo apt-get install build-essential
```

hopefully that will fix your woes....

---

### Post by rogerdrange on 2006-12-27
Yes, it worked! Thank you all, and a special thanks to you, spockrock!

---

### Post by rogerdrange on 2006-12-27
A new problem occured! 

> 
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for pkg-config... /usr/bin/pkg-config
checking for libgnomeui-2.0 librsvg-2.0... Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package librsvg-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `librsvg-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'librsvg-2.0' found
configure: error: Library requirements (libgnomeui-2.0 librsvg-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.


Somebody, please help!

---


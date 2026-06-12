---
title: "Can't open Synaptic error"
date: 2007-07-17
forum: General Help
---

### Post by ZERO_SHIFT on 2007-07-17
I am having problems opening either synaptic or system update. I get an error that I don not understand.

Ca anyone help me?

Thanks in advance

---

### Post by testube_babies on 2007-07-17
Have you tried ```
 sudo apt-get install -f
```

This will resolve unmet dependencies and hopefully remove the offending package.

---

### Post by ThrobbingBrain66 on 2007-07-17
Fire up a terminal and type
```
sudo apt-get remove --purge flameprojecct
```

If it's a package you need, reinstall it afterward
```
sudo apt-get install flameproject
```

---

### Post by ZERO_SHIFT on 2007-07-17
I tried both your suggestions but I am still stuck. Here is what I got:
```
zaid@zaid-laptop:~$  sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flameproject needs to be reinstalled, but I can't find an archive for it.
zaid@zaid-laptop:~$ sudo apt-get remove --purge flameprojecct
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flameproject needs to be reinstalled, but I can't find an archive for it.
```

Any ideas?

Thanks

---

### Post by bapoumba on 2007-07-17
Where did you get that package from ? Looks I cannot find it in the ubuntu repos.
And what is your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by ZERO_SHIFT on 2007-07-17
> **bapoumba said:**
> Where did you get that package from ? Looks I cannot find it in the ubuntu repos.
And what is your sources.list?
```
cat /etc/apt/sources.list
```

Thank you for the reply.

Here is what I got:
```
zaid@zaid-laptop:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe #Added by software-properties

#AUTOMATIX REPOS START

deb http://wine.lowvoice.nl/apt feisty main

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./

## LG3D repsoitories
deb http://javadesktop.org/lg3d/debian stable contrib
# deb http://javadesktop.org/lg3d/debian testing contrib
# deb http://javadesktop.org/lg3d/debian unstable contrib
deb http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu feisty/
deb http://jonnylamb.com/debian/bongo ubuntu-feisty/

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs... 
# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```Thanks

---

### Post by bapoumba on 2007-07-18
Thanks.
Do you know which repo you used to install it in the first place?

The commented debian repos ?
(I suppose you are aware of the problems that _may_ come up with installing packages from other distributions).
If so, enable the repos again, purge the package, and comment all the debian repos after your done.

---

### Post by ZERO_SHIFT on 2007-07-18
> **bapoumba said:**
> Thanks.
Do you know which repo you used to install it in the first place?

The commented debian repos ?
(I suppose you are aware of the problems that _may_ come up with installing packages from other distributions).
If so, enable the repos again, purge the package, and comment all the debian repos after your done.

I really did not understand what you meant. How do I enable repos again?

Thanks

---

### Post by bapoumba on 2007-07-18
> **ZERO_SHIFT said:**
> I really did not understand what you meant. How do I enable repos again?

Thanks
Sorry :)

I have looked for flameprojecct and flameproject in the ubuntu repositories, but I could not find it. I may have not looked properly or you did not install it from ubuntu repositories.
So my question was: where did you get the package from ?

Looking at your sources.list, there are debian repositories LDG3 (I did not look was that is) and some of them are commented, ie there is a # at the beginning of the line, making the repos unavailable. That could explain why the package manager cannot find the package.
Another solution is the treviño repos, that are commented too.

Could you try
```
apt-cache madison flameproject
```
or flameprojecct, to see if you can trace it?

---

### Post by ZERO_SHIFT on 2007-07-18
zaid@zaid-laptop:~$ apt-cache madison flameproject
zaid@zaid-laptop:~$ apt-cache madison flameproject
zaid@zaid-laptop:~$ apt-cache madison flameprojecct
zaid@zaid-laptop:~$ sudo apt-cache madison flameproject
Password:
zaid@zaid-laptop:~$
zaid@zaid-laptop:~$ sudo apt-cache madison flameprojecct
zaid@zaid-laptop:~$

no luck :-(

---

### Post by bapoumba on 2007-07-19
[http://www.flameproject.org/index.php/Main_Page]("http://www.flameproject.org/index.php/Main_Page")
[http://www.flameproject.org/index.php/Support_Contacts]("http://www.flameproject.org/index.php/Support_Contacts")
Sorry, I do not know this package and could not find . May be checking with them would be a good idea (looks like they prefer the mailing list over the forum).

The error does not bring up anything in google. May be try to download it again and install it with dpkg as recommended here:
[http://www.flameproject.org/index.php/How_To_Install]("http://www.flameproject.org/index.php/How_To_Install")

---

### Post by ZERO_SHIFT on 2007-07-20
I still do not understand why a single package will break synaptic?

---

### Post by bapoumba on 2007-07-20
Actually, synaptic or other package managers are not broken. The package is faulty, and the package manager cannot find it to fix it. This is why I asked you where you installed it from, so that you can install it back, or remove it.
Did you try to download the package and install it with dpkg?

---

### Post by ZERO_SHIFT on 2007-07-20
> **bapoumba said:**
> Actually, synaptic or other package managers are not broken. The package is faulty, and the package manager cannot find it to fix it. This is why I asked you where you installed it from, so that you can install it back, or remove it.
Did you try to download the package and install it with dpkg?

I got it from here [http://sourceforge.net/project/downloading.php?group_id=58083&use_mirror=umn&filename=ubuntu.704-flameproject_0.7.7.dev-0ubuntu6_i386.deb&73853126](http://sourceforge.net/project/downloading.php?group_id=58083&use_mirror=umn&filename=ubuntu.704-flameproject_0.7.7.dev-0ubuntu6_i386.deb&73853126)

But I got an error :confused: Check attached image

---

### Post by bapoumba on 2007-07-20
Try this:
```
:~$ sudo dpkg -i ubuntu.704-flameproject_0.7.7.dev-0ubuntu2_i386.deb
```
The error on the screenshot says it may be a permission problem.

---

### Post by ZERO_SHIFT on 2007-07-20
This is what I got:
```
zaid@zaid-laptop:~$ sudo dpkg -i ubuntu.704-flameproject_0.7.7.dev-0ubuntu2_i386.deb
Password:
dpkg: error processing ubuntu.704-flameproject_0.7.7.dev-0ubuntu2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu.704-flameproject_0.7.7.dev-0ubuntu2_i386.deb

```

Any ideas?

Thanks

---

### Post by bapoumba on 2007-07-21
I'm afraid I've run out of ideas. If dpkg cannot install the .deb file you have downloaded, the last alternative is to compile it from sources...

Did you run dpkg -i from the directory you had downloaded the file to ?

---

### Post by yorkie on 2007-07-21
[http://www.flameproject.org/index.php/Main_Page](http://www.flameproject.org/index.php/Main_Page)
hope this is what you are looking for

---

### Post by ZERO_SHIFT on 2007-07-21
> **bapoumba said:**
> Did you run dpkg -i from the directory you had downloaded the file to ?

No I just ran it from terminal.  What directory should I be in?:-k

---

### Post by Nythain on 2007-07-21
the directory actually containing the .deb file... wherever you downloaded it to (if you still have it)
cd to that directory and run the sudo dpkg -i command again and see what it says them

---

### Post by ZERO_SHIFT on 2007-07-22
Where can I find the directory I looked in the hidden files in /home but no luck.

---

### Post by ZERO_SHIFT on 2007-07-24
I am really stuck please help me out here.
](*,)
Danke

---

### Post by theduke0 on 2007-07-26
i have a very similar problem to this.  

i had downloaded a driver for a brother printer and attempted to follow the directions on the brother website, but they didn't work that great.  the error i have now is exactly like you are describing.  i know what is happening, i just don't know of a solution.  

I would love to install this printer driver, but I am more concerned with making my package management stuff work again.  

When I attempt to install the package using dpkg, here is the output:

[email]david@smokey:~/.prin[/email]ter$ sudo dpkg -i hl5170dnlpr-1.1.2-1.i386.deb 
Password:
(Reading database ... 154890 files and directories currently installed.)
Preparing to replace hl5170dnlpr 1.1.2-1 (using hl5170dnlpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl5170dnlpr ...
/var/lib/dpkg/info/hl5170dnlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl5170dnlpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl5170dnlpr-1.1.2-1.i386.deb


when I try all of the solution suggested thus far in this post, I get:

[email]david@smokey:~/.prin[/email]ter$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package hl5170dnlpr needs to be reinstalled, but I can't find an archive for it.
[email]david@smokey:~/.prin[/email]ter$ 

Please help.

---

### Post by ZERO_SHIFT on 2007-07-26
```
zaid@zaid-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package flameproject needs to be reinstalled, but I can't find an archive for it.

```

Please help us! we want synaptic back.

Anyone?!

:(

---

### Post by ZERO_SHIFT on 2007-07-26
I think I am getting somewhere:

```
zaid@zaid-laptop:~$ sudo dpkg --remove --force-remove-reinstreq ubuntu.704-flameproject_0.7.7.dev-0ubuntu2_i386.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

```

Any ideas?

---

### Post by theduke0 on 2007-07-26
i get that same error, but i just don't know what to do with it.  

any ideas?

---

### Post by theduke0 on 2007-07-26
I have a solution!

So I needed to install 2 files so that the proper files were needed when installed the package I was talking about above.  I ended up digging through some other brother walkthoughs and realized that I needed to create a symbolic link to another file!  whew.  

I would like to know how to remove a package that does this in the future in case i have another faulty install, but for now -- i will just stick to fixing the install and then moving forward.

---


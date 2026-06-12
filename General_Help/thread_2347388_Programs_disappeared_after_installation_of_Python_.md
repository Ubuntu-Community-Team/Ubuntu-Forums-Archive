---
title: "Programs disappeared after installation of Python 3.6"
date: 2016-12-24
forum: General Help
---

### Post by hellerickferlibay on 2016-12-24
A noobish user of Ubuntu 16.10 here.

Yesterday Python 3.6 was released and I wanted to check it. There was nobody to tell me that it could be dangerous. So I downloaded it, unpacked it, and executed commands:

```
./configure
make
make install
```

Everything seemed fine. Currently I have working versions of Python 2.7, Python 3.5, Python 3.6. The default version is 3.5.2 (at least that's what I get after typing "python" in the command line).

The problem is, it looks like some software disappeared from the system and cannot be restored: Gimp, Inkscape, Zim Desktop Wiki etc.

Command "sudo apt-get install gimp" causes such response:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gimp : Depends: python-gtk2 (>= 2.8.0) but it is not going to be installed
        Depends: python:any (>= 2.6.6-7~)
E: Unable to correct problems, you have held broken packages.
```

There were also some system updates applied, I'm not sure if it matters.

So what I'm supposed to do now?

I'm sorry if I'm asking in a wrong place.

---

### Post by dragonfly41 on 2016-12-24
If you are installing multiple versions of python I suggest reading the discussions in closing posts
in this thread ... [https://ubuntuforums.org/showthread.php?t=2346558](https://ubuntuforums.org/showthread.php?t=2346558)
where I suggest using miniconda as the Python installer.

Of course you can still install multiple python manually from Ubuntu repo as you have done.
It is just that miniconda makes the installation task much easier, sorting our conflicts
between versions of python.   And versions of python can be switched on the fly.

---

### Post by mc4man on 2016-12-24
Your manual install of python would not have removed packages, at worst would just affect opening/running things,  if at all.
Maybe install aptitude (sudo apt install aptitude) then use it to attempt to install gimp or better yet python-gtk2
It may be a bit more verbose as to what's preventing the install.

---

### Post by hellerickferlibay on 2016-12-24
Errors, conflicts...

```
hellerick@hellerick-C17A:~$ sudo aptitude install python-gtk2
[sudo] password for hellerick: 
The following NEW packages will be installed:
  libpython-stdlib:i386{a} libpython2.7-minimal:i386{a} 
  libpython2.7-stdlib:i386{a} libreadline7:i386{a} python:i386{ab} 
  python-cairo{ab} python-gobject-2{ab} python-gtk2{b} 
  python-minimal:i386{ab} python2.7:i386{ab} python2.7-minimal:i386{ab} 
The following partially installed packages will be configured:
  tex-common 
0 packages upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 4 960 kB of archives. After unpacking 21,9 MB will be used.
The following packages have unmet dependencies:
 python2.7-minimal : Conflicts: python2.7-minimal:i386 but 2.7.12-3build1 is to be installed
 python2.7-minimal:i386 : Conflicts: python2.7-minimal but 2.7.12-3build1 is installed
 python2.7 : Conflicts: python2.7:i386 but 2.7.12-3build1 is to be installed
 python2.7:i386 : Conflicts: python2.7 but 2.7.12-3build1 is installed
 python-cairo : Depends: python (< 2.8) but 3.6.0-1 is installed
 python : Conflicts: python:i386 but 2.7.11-2 is to be installed
 python:i386 : Conflicts: python but 3.6.0-1 is installed
 python-gtk2 : Depends: python (< 2.8) but 3.6.0-1 is installed
 python-gobject-2 : Depends: python (< 2.8) but 3.6.0-1 is installed
 python-minimal : Conflicts: python-minimal:i386 but 2.7.11-2 is to be installed
 python-minimal:i386 : Conflicts: python-minimal but 2.7.11-2 is installed
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     python:i386 [Not Installed]                        
2)     python-cairo [Not Installed]                       
3)     python-gobject-2 [Not Installed]                   
4)     python-gtk2 [Not Installed]                        
5)     python-minimal:i386 [Not Installed]                
6)     python2.7:i386 [Not Installed]                     
7)     python2.7-minimal:i386 [Not Installed]             

     Leave the following dependencies unresolved:         
8)     python-minimal:i386 recommends python:i386         
9)     python2.7-minimal:i386 recommends python2.7:i386   



Accept this solution? [Y/n/q/?] Y
The following partially installed packages will be configured:
  tex-common 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up tex-common (6.05) ...         
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building format(s) --all.
    This may take some time... 
fmtutil failed. Output has been stored in
/tmp/fmtutil.LnyjDKtO
Please include this file if you report a bug.

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
Setting up tex-common (6.05) ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building format(s) --all.
    This may take some time... 
fmtutil failed. Output has been stored in
/tmp/fmtutil.DShceyh9
Please include this file if you report a bug.

dpkg: error processing package tex-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tex-common
```

---

### Post by mc4man on 2016-12-24
What does this show
```
apt-cache policy python python3 python3.5 python3.6
```

---

### Post by hellerickferlibay on 2016-12-24
```
hellerick@hellerick-C17A:~$ apt-cache policy python python3 python3.5 python3.6
python:
  Installed: 3.6.0-1
  Candidate: 3.6.0-1
  Version table:
 *** 3.6.0-1 100
        100 /var/lib/dpkg/status
     2.7.11-2 500
        500 http://linux.nsu.ru/ubuntu yakkety/main amd64 Packages
python3:
  Installed: 3.5.1-4
  Candidate: 3.5.1-4
  Version table:
 *** 3.5.1-4 500
        500 http://linux.nsu.ru/ubuntu yakkety/main amd64 Packages
        100 /var/lib/dpkg/status
python3.5:
  Installed: 3.5.2-6
  Candidate: 3.5.2-6
  Version table:
 *** 3.5.2-6 500
        500 http://linux.nsu.ru/ubuntu yakkety/main amd64 Packages
        100 /var/lib/dpkg/status
python3.6:
  Installed: 3.6.0~b2-1
  Candidate: 3.6.0~b2-1
  Version table:
 *** 3.6.0~b2-1 500
        500 http://linux.nsu.ru/ubuntu yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by mc4man on 2016-12-24
You already had python-3.6 installed as it's available in 16.10 so not sure why you built & installed from source. You could try going back to that _source folder you built &  installed from_ & run this, maybe it'll uninstall the self build you did
```
sudo make uninstall
```

---

### Post by hellerickferlibay on 2016-12-24
Python 3.6 was released this Friday. I doubt I could have it.

---

### Post by mc4man on 2016-12-24
> **hellerickferlibay said:**
> Python 3.6 was released this Friday. I doubt I could have it.
> 
python3.6:
  Installed: 3.6.0~b2-1
  Candidate: 3.6.0~b2-1
  Version table:
 *** 3.6.0~b2-1 500
        500 [http://linux.nsu.ru/ubuntu](http://linux.nsu.ru/ubuntu) yakkety/universe amd64 Packages
        100 /var/lib/dpkg/status
You have the 3.6 beta 2 installed

This is your bigger issue - 
> python:
  Installed: 3.6.0-1
  Candidate: 3.6.0-1
  Version table:
 *** 3.6.0-1 100
        100 /var/lib/dpkg/status
     2.7.11-2 500
        500 [http://linux.nsu.ru/ubuntu](http://linux.nsu.ru/ubuntu) yakkety/main amd64 Packages

As I said remove your build & likely gimp,ect can be installed. Otherwise check update-alternatives to see if there is an alternative for python
```
sudo update-alternatives --all
```
Go thru & maybe there is one, by default there wouldn't be.. as Ubuntu sets python2.7 as the default for "python"

Or possibly check /usr/local/bin for the python symlink, if there & pointing to python3.6 then get rid of it. 

Best would be to remove your self build.

---

### Post by mc4man on 2016-12-24
The other possibility is you've installed a package named python  & it's  version is 3.6.0-1
That couldn't have come from Ubuntu & didn't just install itself so I'd assume you know that you did?
run this
```
which python && python --version
```

Should return - 
/usr/bin/python
Python 2.7.12+

which python3 && python3 --version

should return
/usr/bin/python3
Python 3.5.2+

---

### Post by hellerickferlibay on 2016-12-24
So the two versions did install nearly simultaneously? Huh.

Calling "sudo make uninstall" from my installation folder causes message: "make: *** No rule to make target 'uninstall'.  Stop."

There were indeed two sets of python3.6 files in /usr/local/bin folder. I did remove those titled as "python3.6m". When I run python3.6 it greets me as "Python 3.6.0 (default, Dec 23 2016, 19:28:39)".

But when I type "idle-python3.6" it still calls the version 3.6.0b2 and the problem is not solved.

---

### Post by hellerickferlibay on 2016-12-24
"which python && python --version" returns:
```
/home/hellerick/miniconda3/bin/python
Python 3.5.2 :: Continuum Analytics, Inc.
```

"which python3 && python3 --version" returns:
```
/home/hellerick/miniconda3/bin/python3
Python 3.5.2 :: Continuum Analytics, Inc.
```

Whoah, Miniconda involved. And in weird way, it seems.

---

### Post by dragonfly41 on 2016-12-24
Re: your discovered installation of miniconda (that is odd) ... perhaps you followed my suggestion in post#2

Run this command to list your miniconda installations

conda info -e

and since you have miniconda3 installed (not miniconda2) this installation defaults root to python3x.
That is why you can't run python2.7.

You will need to create an explicit python2.7 env in miniconda3 (read the docs).   Mine is called py27_32  .. a 32bit version.

then switch to it using command
source activate py27_32

and you can switch back to root using command
source activate root.

---

### Post by hellerickferlibay on 2016-12-24
I did create a Python 2.7 for Miniconda.

Now "conda info -e" says:
```

(py27) hellerick@hellerick-C17A:~$ conda info -e
# conda environments:
#
py27                  *  /home/hellerick/miniconda3/envs/py27
root                     /home/hellerick/miniconda3

```

Not sure if it was a good idea, but I attempted to install Gimp from Py32. It gave me:

```

(py27) hellerick@hellerick-C17A:~$ sudo aptitude install gimp
The following NEW packages will be installed:
  gimp gimp-data{a} libamd2{a} libbabl-0.1-0{a} libcamd2{a} libccolamd2{a} 
  libcholmod3{a} libgegl-0.3-0{a} libgimp2.0{a} libmetis5{a} 
  libpython-stdlib:i386{a} libpython2.7-minimal:i386{a} 
  libpython2.7-stdlib:i386{a} libreadline7:i386{a} libumfpack5{a} 
  python:i386{ab} python-cairo{ab} python-gobject-2{ab} python-gtk2{ab} 
  python-minimal:i386{a} python2.7{ab} python2.7:i386{ab} 
  python2.7-minimal{ab} python2.7-minimal:i386{ab} 
0 packages upgraded, 24 newly installed, 0 to remove and 0 not upgraded.
Need to get 20,7 MB of archives. After unpacking 107 MB will be used.
The following packages have unmet dependencies:
 python2.7-minimal : Conflicts: python2.7-minimal:i386 but 2.7.12-3build1 is to be installed
 python2.7-minimal:i386 : Conflicts: python2.7-minimal but 2.7.12-3build1 is to be installed
 python2.7 : Conflicts: python2.7:i386 but 2.7.12-3build1 is to be installed
 python2.7:i386 : Conflicts: python2.7 but 2.7.12-3build1 is to be installed
 python-cairo : Depends: python (< 2.8) but 3.6.0-1 is installed
 python : Conflicts: python:i386 but 2.7.11-2 is to be installed
 python:i386 : Conflicts: python but 3.6.0-1 is installed
 python-gtk2 : Depends: python (< 2.8) but 3.6.0-1 is installed
 python-gobject-2 : Depends: python (< 2.8) but 3.6.0-1 is installed
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      gimp [Not Installed]                               
2)      python:i386 [Not Installed]                        
3)      python-cairo [Not Installed]                       
4)      python-gobject-2 [Not Installed]                   
5)      python-gtk2 [Not Installed]                        
6)      python2.7 [Not Installed]                          
7)      python2.7-minimal [Not Installed]                  

      Leave the following dependencies unresolved:         
8)      python2.7-minimal recommends python2.7             
9)      python-minimal:i386 recommends python:i386         
10)     gimp-data recommends gimp                          



Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

With no visible effect.

BTW, I run Synaptic Package Manager. And it says:

>  [IMG]http://i.imgur.com/PhnYVpG.png[/IMG]

It looks like it think the beta versions are still the latest available. I think I did remove those yesterday, but something reinstalled them.

---

### Post by mc4man on 2016-12-25
```
apt-cache policy python:i386 python
```
post

---

### Post by hellerickferlibay on 2016-12-25
```
hellerick@hellerick-C17A:~$ apt-cache policy python:i386 python
python:i386:
  Installed: (none)
  Candidate: 2.7.11-2
  Version table:
     2.7.11-2 500
        500 [http://linux.nsu.ru/ubuntu](http://linux.nsu.ru/ubuntu) yakkety/main i386 Packages
python:
  Installed: 3.6.0-1
  Candidate: 3.6.0-1
  Version table:
 *** 3.6.0-1 100
        100 /var/lib/dpkg/status
     2.7.11-2 500
        500 [http://linux.nsu.ru/ubuntu](http://linux.nsu.ru/ubuntu) yakkety/main amd64 Packages

```

---

### Post by hellerickferlibay on 2016-12-26
I don't know what's happening but today I managed to re-install the programs I'd lost.

So practically I see no problem anymore other than still having two Python 3.6 installed. When I run "idle-python3.6" I still get the 3.6.0b2 version. I wish I could get rid of it.

---

### Post by mc4man on 2016-12-26
> **hellerickferlibay said:**
> I don't know what's happening but today I managed to re-install the programs I'd lost.

So practically I see no problem anymore other than still having two Python 3.6 installed. When I run "idle-python3.6" I still get the 3.6.0b2 version. I wish I could get rid of it.
Install & use synaptic, search python, look around, ect.

---

### Post by ian-weisser on 2016-12-26
> **hellerickferlibay said:**
> There was nobody to tell me that it could be dangerous.

You should take on this task in the community: The fellow who warns new users about that.

---

### Post by dragonfly41 on 2016-12-26
post#18

> [COLOR=#000000]Install & use synaptic, search python, look around, ect.[/COLOR][COLOR=#000000]

Unfortunately that can give incomplete results since Synaptic will not show miniconda installations.

I think your packages "disappeared" because (default) python-2.7 (from repo, not miniconda) was removed by you (or pushed out of default status by your installation of python-3.6) making the packages (which may require python-2.7) inoperable.

sudo updatedb .. and wait for about 5 minutes for updatedb to index all recent files
then
sudo locate bin/python

This shows all python binaries (including miniconda envs)

also a script run in each python version will show paths ..

[/COLOR]
```
python2.7 -c &#8216;import sys; print("\n".join(sys.path))&#8217;

or in console ..
python2.7
>>> import sys; 
>>> print("\n".join(sys.path));
```

Repeat running script in console for each python version .. python, python2.7, python3.5, python3.6 .. 

And look for python path using .. echo $PATH

Final point, you can find the dependencies of apps by using ldd.

---

### Post by mc4man on 2016-12-27
> **dragonfly41 said:**
> 

Unfortunately that can give incomplete results since Synaptic will not show miniconda installations.


He was asking about "3.6.0b2 version" which most assuredly is in [synaptic ]("https://ubuntuforums.org/showthread.php?t=2347388&p=13586806&viewfull=1#post13586806")

---

### Post by dragonfly41 on 2016-12-28
True enough (at least in Ubuntu 16.04, not in my older Ubuntu 14.04).
I was suggesting that Synaptic does not give me a picture of manually installed apps.
And with Ubuntu 14.04 there are quite a few, to keep up with latest releases.

[Later Edit]
To those users interested in miniconda, today I installed python 3.6 (on Ubuntu 14.04 32bit) as miniconda environment by this miniconda command ...

```

conda create -n py36 python=3.6

The following NEW packages will be INSTALLED:


    openssl:    1.0.2j-0     
    pip:        9.0.1-py36_1 
    python:     3.6.0-0      
    readline:   6.2-2        
    setuptools: 27.2.0-py36_0
    sqlite:     3.13.0-0     
    tk:         8.5.18-0     
    wheel:      0.29.0-py36_0
    xz:         5.2.2-0      
    zlib:       1.2.8-3   


```

---


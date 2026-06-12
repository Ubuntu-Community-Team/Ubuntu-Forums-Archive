---
title: "can't install build essential"
date: 2005-07-27
forum: General Help
---

### Post by raakken on 2005-07-27
Hi!
I resently installed ubuntu, and i love it(but it's abit slow, anyone can help me with that to? fluxbox etc???) But i have problems with installing build essential, I get thjis error:
fredrik@ubuntu:~$ sudo aptitude install build essential
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find package "build", and more than 40
packages contain "build" in their name.
Couldn't find package "essential".  However, the following
packages contain "essential" in their name:
  build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NO:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done


I hvae problems compiling new app's from source too, this is because of this?
Hope someone can help me
thans

---

### Post by majikstreet on 2005-07-27
[QUOTE=raakken]Hi!
I resently installed ubuntu, and i love it(but it's abit slow, anyone can help me with that to? fluxbox etc???) But i have problems with installing build essential, I get thjis error:
fredrik@ubuntu:~$ sudo aptitude install build essential
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
Couldn't find package "build", and more than 40
packages contain "build" in their name.
Couldn't find package "essential".  However, the following
packages contain "essential" in their name:
  build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_NO:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done


I hvae problems compiling new app's from source too, this is because of this?
Hope someone can help me
thans[/QUOTE]
 Are your [repositories enabled](http://ubuntuguide.org/#extrarepositories)?

---

### Post by PMO6022 on 2005-07-27
[QUOTE=raakken]Hi!
I resently installed ubuntu, and i love it(but it's abit slow, anyone can help me with that to? fluxbox etc???) But i have problems with installing build essential, I get thjis error:
fredrik@ubuntu:~$ sudo aptitude install build essential
[/QUOTE]
 Try: sudo aptitude install build-essential

When you type it without the hyphen, aptitide looks for a program named "build" and another program named "essential"

And yes, this could very well explain why you can't build from source.

---

### Post by raakken on 2005-07-27
Hi
tried aptitude, but I got this error:
fredrik@ubuntu:~$ sudo aptitude install build-essential
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not installable or
                            libc-dev which is a virtual package.
                   Depends: g++ (>= 3:3.3) but it is not installable

g++ doesn't install couse I need some file, and I can't install that file, couse it needs g++ , so you can see why I'm frustrated

---

### Post by PMO6022 on 2005-07-27
check your repositories according to majikstreet's link, then type ```
sudo apt-get update
sudo apt-get install build-essential
```
although you really should only need the "main" repo; build-essential, libc6-dev, and g++ are all in there.

You can also try synaptic, although I can't help you there, it is just a front-end for apt-get

I guess if things are really broken you could try an apt-get dist-upgrade...really just a last resort.  Read up on the dist-upgrade before doing it.

---

### Post by az on 2005-07-27
sudo apt-get -f install

---

### Post by raakken on 2005-07-28
doesn't do anything...

---


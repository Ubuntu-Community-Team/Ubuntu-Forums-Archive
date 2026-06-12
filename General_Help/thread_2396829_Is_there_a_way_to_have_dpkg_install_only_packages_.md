---
title: "Is there a way to have dpkg install only packages whose dependencies are ok?"
date: 2018-07-21
forum: General Help
---

### Post by raphaell2 on 2018-07-21
Hi, 

I'm using Xubuntu 18.04. I have a large collection of .deb files I got from the apt archive on my pc, mainly in the hope that, if I should have to reinstall, I might need to download less. Now, if I have I number of .deb files in a directory, is there a way of automatically installing only those of them that don't have any outstanding unresolved dependencies? I could, of course, try to turn the directory into a local apt repository, but, frankly, all the instructions I've seen for that kind of thing were extremely complicated. Is there an easier way?

---

### Post by Dennis N on 2018-07-21
Use **GDebi** package installer for the .deb files. It will fetch needed dependencies from the repos. If it cannot satisfy them, it will inform you of unmet dependencies or conflicts. If there are none, you have to OK the install before it begins.

---

### Post by raphaell2 on 2018-07-21
Good idea, but GDebi doesn't really work with multiple packages at once, and installing one package at a time for thousands of packages is impractical.

---

### Post by &amp;KyT$0P# on 2018-07-21
You could try this -
```
sudo apt install [COLOR="#FF0000"]/path/to/directory/containing/the/packages/*.deb[/COLOR]
```

---

### Post by raphaell2 on 2018-07-22
> **halogen2 said:**
> You could try this -
```
sudo apt install [COLOR=#FF0000]/path/to/directory/containing/the/packages/*.deb[/COLOR]
```

Thank you, but when I try this I get a complaint about too many arguments. And when I try to reduce the number of arguments by breaking it up into steps - i.e. 

```
sudo apt install [COLOR=#FF0000]/path/to/directory/containing/the/packages/a*.deb[/COLOR]
```

the software tries to install older versions of packages over already installed newer versions. 


What I'd like to have is a command that goes through the list of .deb files and, for each file, first checks whether that version of that package or a newer version is already installed, then, if the answer to that is no, checks whether the package has any unresolved dependencies, and, if the answer to that is no, too, installs the package, and then moves on to the next package. For the first part of that, 

```
sudo dpkg -GERi [COLOR=#FF0000]/path/to/directory/containing/the/packages/[/COLOR]
``` 

works fine, but it doesn't do the last part.

---

### Post by kazakore on 2018-07-22
Does
```
sudo dpkg -GERi [COLOR=#FF0000]/path/to/directory/containing/the/packages/[/COLOR]
```
only stop working when it find a package it wont install or always stop? -R should install all in the directory (Recursive) so seems strange it doesn't move to next file.

Remember you can always use --no-act to simulate the action and see what it will do.


If you can't get that to work ould something like
```
[FONT=arial]
sudo find /path/to/debs -name '*.deb' -exec sh -c 'for f; do dpkg -GEi "$f"; done' find-sh {} +
[/FONT]
```[FONT=arial]
perhaps do it?

Not sure if the sudo relates to the -exec part. You might need to run
```
sudo -i
```
first to give you a root shell and run without sudo at the start.


Edit: Yeah seems to work when doing a simulation run here:
```

$ sudo find /.../Downloads/debs/ -name '*.deb' -exec sh -c 'for f; do dpkg -GEi --no-act "$f"; done' find-sh {} +
[sudo] password for xxxx: 
dpkg: will not downgrade kxstudio-repos from 9.5.1~kxstudio3 to 9.2.2~kxstudio1, skipping
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../mixxx-2.1.1-artful-amd64.deb ...
dpkg: version 9.5.1~kxstudio3 of kxstudio-repos-gcc5 already installed, skipping
dpkg: will not downgrade mixxx from 2.1.1-0ubuntu1~2.1~git6743~bionic to 2.1.0~rc1-ppa1~2.1~git6676~artful, skipping
dpkg: will not downgrade puddletag from 1.2.0-1 to 1.0.5, skipping
dpkg: will not downgrade mixxx from 2.1.1-0ubuntu1~2.1~git6743~bionic to 2.1.0~alpha~pre-ppa1~master~git6403~xenial, skipping
Selecting previously unselected package leap-archive-keyring.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../leap-archive-keyring_2016.03.08_all.deb ...
Selecting previously unselected package atom.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../Downloads/debs/atom-amd64.deb ...
dpkg: will not downgrade mp3gain from 1.5.2-r2-6~bionic1.0 to 1.5.2-r2-2+deb7u1, skipping
Selecting previously unselected package python-support.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../python-support_1.0.15_all.deb ...
Selecting previously unselected package bitwig-studio.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../debs/bitwig-studio-2.2.2.deb ...
Selecting previously unselected package easymp3gain-data.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../easymp3gain-data_0.5.0+svn135-6_all.deb ...
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../mixxx-2.2.0-alpha-pre-master-release-artful-amd64-latest.deb ...
dpkg: will not downgrade mixxx from 2.1.1-0ubuntu1~2.1~git6743~bionic to 2.1.0-ppa1~2.1~git6681~artful, skipping
dpkg: version 9.5.1~kxstudio3 of kxstudio-repos already installed, skipping
dpkg: will not downgrade kxstudio-repos-gcc5 from 9.5.1~kxstudio3 to 9.2.2~kxstudio1, skipping
Selecting previously unselected package aarddict.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../debs/aarddict_0.9.3-1_all.deb ...
dpkg: will not downgrade libthunarx-2-0 from 1.6.15-0ubuntu1 to 1.6.3-1ubuntu5, skipping
Selecting previously unselected package mullvad.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../debs/mullvad_67-1_all.deb ...
Selecting previously unselected package fbreader.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../fbreader_0.99.4-1_amd64.deb ...
dpkg: will not downgrade waterfox from 56.2.2 to 56.1.0, skipping
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../mp3gain_1.5.2-r2-6_amd64.deb ...
Selecting previously unselected package lightworks.
(Reading database ... 479591 files and directories currently installed.)
Preparing to unpack .../debs/lwks-14.0.0-amd64.deb ...

```[/FONT]

---

### Post by raphaell2 on 2018-07-22
> **kazakore said:**
> Does
```
sudo dpkg -GERi [COLOR=#FF0000]/path/to/directory/containing/the/packages/[/COLOR]
```
only stop working when it find a package it wont install or always stop? -R should install all in the directory (Recursive) so seems strange it doesn't move to next file.


Oh, at first it works without stopping. It tries to install *all* packages- including the ones with unresolved dependencies. While it's doing that, it gradually collects more and more error messages. Eventually, it has enough errors to abort, and leaves behind a lot of unpacked but not yet configured packages, many of which have unresolved dependencies, and some of which are so messed up that even apt's standard package repair tools can't repair them anymore. At that point, apt usually stops working completely, and the only way to save the system is to completely reinstall the OS. 


> Remember you can always use --no-act to simulate the action and see what it will do.


If you can't get that to work ould something like
```
[FONT=arial]
sudo find /path/to/debs -name '*.deb' -exec sh -c 'for f; do dpkg -GEi "$f"; done' find-sh {} +
[/FONT]
```[FONT=arial]
perhaps do it?

Not sure if the sudo relates to the -exec part. You might need to run
```
sudo -i
```
first to give you a root shell and run without sudo at the start.


Edit: Yeah seems to work when doing a simulation run here:
```

[code][FONT=arial]
sudo find /path/to/debs -name '*.deb' -exec sh -c 'for f; do dpkg -GEi "$f"; done' find-sh {} +
[/FONT]
```[FONT=arial]
perhaps do it?

Not sure if the sudo relates to the -exec part. You might need to run
```
sudo -i
```
first to give you a root shell and run without sudo at the start.[/FONT][/code][/FONT]

I haven't tried that yet; thank you.

---

### Post by raphaell2 on 2018-07-22
kazakore, does your code include a way of checking if a package has unresolved dependencies before installing it?

---

### Post by deadflowr on 2018-07-22
Where are you getting the packages from, apt archive wise?

---

### Post by raphaell2 on 2018-07-22
> **deadflowr said:**
> Where are you getting the packages from, apt archive wise?

They all (except for one) originally came from my /var/cache/apt/archives folder, all collected under Xubuntu 18.04. Before that, they were all in the regular Xubuntu 18.04 repository servers. The one exception is fvd-module, from the website of the fvd firefox extension, but that one works well regularly. 

My hope with that .deb archive is simply to reduce the number of files I need to download if I want to do a reinstall (or perhaps, in the future, an installation on some new computer).

---

### Post by deadflowr on 2018-07-22
Then repopulate them into the new /var/cache/apt/archives location and then run an apt-get update
Then run an apt-get dist-upgrade,
and see how much will be needed to download.
it should be a significantly low number, depending on how much archives you had.


> does your code include a way of checking if a package has unresolved dependencies before installing it?
apt will always tell you if a package requires any new packages as dependencies.

---

### Post by kazakore on 2018-07-22
> **raphaell2 said:**
> kazakore, does your code include a way of checking if a package has unresolved dependencies before installing it?

Doesn't dpkg always check for dependencies and not install if they are missing unless you specifically tell it to ignore a dependency? I admit I took the dpkg command from your comment and then just double-checked what the arguments do on their manpage. I can't see anything to specifically skip if a dependency is missing, but as I said I thought it always does so by default....

Hopefully somebody else will confirm.

---

### Post by deadflowr on 2018-07-22
> Doesn't dpkg always check for dependencies 
No, or rather not before it runs.
dpkg does not care about dependency issues until it crosses them during a package's installation.

apt on the other hand will tell you before you start installing something whether or not dependencies are needed or need to be fixed or what have you.

---

### Post by kazakore on 2018-07-22
> **deadflowr said:**
> 
apt on the other hand will tell you before you start installing something whether or not dependencies are needed or need to be fixed or what have you.

So I take it my earlier script could replace dpkg with apt. Would that also automatically check the versions??

---

### Post by raleigh3 on 2018-07-22
> **raphaell2 said:**
> Hi, 

I'm using Xubuntu 18.04. I have a large collection of .deb files I got from the apt archive on my pc, mainly in the hope that, if I should have to reinstall, I might need to download less. Now, if I have I number of .deb files in a directory, is there a way of automatically installing only those of them that don't have any outstanding unresolved dependencies? I could, of course, try to turn the directory into a local apt repository, but, frankly, all the instructions I've seen for that kind of thing were extremely complicated. Is there an easier way?

You are better off making backup images using something like Clonezilla.

---


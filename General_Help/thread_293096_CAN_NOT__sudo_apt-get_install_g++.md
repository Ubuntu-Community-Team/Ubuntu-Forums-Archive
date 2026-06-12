---
title: "CAN NOT : sudo apt-get install g++"
date: 2006-11-04
forum: General Help
---

### Post by stevand on 2006-11-04
I was able just few days ago to navigate through the installation instructions and I was able to instal on my laptop DX, Octave and g++ .
I did not instal MPlayers and other packages.

Then I did the sam with my desktop .. however I did not install first g++ and I did not follow the same order but I did throug the Synaptic Package menager as it was more easy for me ....

THEN a big proble came when I tried to install some blitz vector package
since it gave me the following message 

"
stevand@stevand-desktop:~/Desktop/blitz-0.9$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
configure:

Configuring blitz 0.9 for i686-pc-linux-gnulibc1


checking for xlc++... no
checking for xlC... no
checking for icpc... no
checking for icc... no
checking for pathCC... no
checking for cxx... no
checking for aCC... no
checking for c++... no
checking for CC... no
checking for g++... no
checking for pgCC... no
checking for KCC... no
checking for FCC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.

"

Then I tried to install g++ and the following message shows up 

stevand@stevand-desktop:~/Desktop/blitz-0.9$ sudo apt-get install g++
Password:
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
  g++: Depends: g++-4.0 (>= 4.0.3) but it is not going to be installed
E: Broken packages

"

I d not know how to file a bug report or at leass to specify what is the bug .... moreover I would appriciate if someone can bring me back to the core disc installation or the basic one that will me allow to use g++

THANK since I am now ](*,)

---

### Post by Sef on 2006-11-04
Have you installed build-essential?

sudo apt-get update

sudo aptitude install build-essential

---


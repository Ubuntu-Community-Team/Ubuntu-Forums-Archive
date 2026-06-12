---
title: "Adjusting /etc/ld.so.config so libraries work with programs?"
date: 2007-10-16
forum: General Help
---

### Post by lazcisco on 2007-10-16
So this is what is currently in /etc/ld.so.config
include /etc/ld.so.conf.d/*.conf

I was changing some things around, because when I tried to use root and geant4, I kept getting error messages like these:

/usr/local/bin/root.exe: error while loading shared libraries: libCore.so.5.17: cannot open shared object file: No such file or directory
error while loading shared libraries: libCLHEP-2.0.3.1.so: cannot open shared object file: No such file or directory


I read that including /usr/local/lib/root/ in ld.so.config would fix this, but that didn't work. What can I do to fix this? I also think ldconfig in terminal would work as well, but I'm not quite sure how to go about that either.

---

### Post by jalirious on 2007-10-30
No help I'm afraid, but on a fresh install of gutsy the root package made by Christian Holm for root 5.16;
                                [http://mirror.phy.bnl.gov/debian-root/](http://mirror.phy.bnl.gov/debian-root/) 

worked like a charm (after installing g++, g77, minuit from synaptic)

Regarding Geant4, I remember installing it on dapper. Managed in the end, but took me ages. Anyone fancy writing a debian package?

[EDIT -> [http://wiki.debian.org/DebianScienceGeant4?highlight=%28geant4%29]](http://wiki.debian.org/DebianScienceGeant4?highlight=%28geant4%29]) Although I have not managed to get this working.

 Trying to install Kevin McCarty's Geant4 8.2 package on my i486 ubuntu 7.10 machine. My 
version of gcc is 4.1.3. I added the following repositories to my sources.list;

deb [http://borex.princeton.edu/~kmccarty/](http://borex.princeton.edu/~kmccarty/) unstable geant4
deb-src [http://borex.princeton.edu/~kmccarty/](http://borex.princeton.edu/~kmccarty/) unstable geant4
deb [http://www-zeus.desy.de/~ferrando/debian/](http://www-zeus.desy.de/~ferrando/debian/) testing hep
deb-src [http://www-zeus.desy.de/~ferrando/debian/](http://www-zeus.desy.de/~ferrando/debian/) testing hep

Unfortunately, after apt-get update && apt-get install geant4;

The following packages have unmet dependencies.
  geant4: Depends: libgeant4-dev but it is not going to be installed
          Depends: libgeant4-plists-dev but it is not going to be installed
          Depends: libg4opengl-dev but it is not going to be installed
          Depends: geant4-examples but it is not going to be installed
E: Broken packages

When I attempt to install these packages (either through apt-get or synaptic) they 
themselves have unmet dependencies;
The following packages have unmet dependencies;

  libgeant4-dev: Depends: clhep2-dev (< 2.0.3.1.0~) but 2.0.3.2-1 is to be installed
                 Depends: libgeant4-4.9-0 (= 4.9.0-1) but it is not going to be installed
E: Broken packages

chlep installs fine, but does not effect the problem above.

[EDIT 2]

Just take out 
deb [http://www-zeus.desy.de/~ferrando/debian/](http://www-zeus.desy.de/~ferrando/debian/) testing hep
deb-src [http://www-zeus.desy.de/~ferrando/debian/](http://www-zeus.desy.de/~ferrando/debian/) testing hep

'You DO NOT need to add a line for his repository to /etc/apt/sources.list, since I've made them available in my repository as a convenience. Indeed, adding his repository in your sources.list may cause trouble because he sometimes distributes versions of CLHEP2 newer than those supported by Geant4.' Kevin McCarty.

Hopefully leaving my spastic antics up here might help someone.

---


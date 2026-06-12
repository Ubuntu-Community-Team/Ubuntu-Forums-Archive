---
title: "Steam dependencies not installing"
date: 2015-10-25
forum: General Help
---

### Post by mattig89ch on 2015-10-25
Hidy ho all,

I tried installing steam, for if/when I have the free time to play some games.  But every time I start it, I get a window with the following text:

Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for matt: 
.................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
  unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                                 Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Do i have to manually install these dependencies?  If so, is it as simple as
sudo get (package name)

or is it more complicated?

---


---
title: "octave installation problems"
date: 2008-05-17
forum: General Help
---

### Post by yang on 2008-05-17
When I try to install the octave3.0 package, I get messages from apt about broken dependencies and whether to accept solutions with negative scores.  I've tried on two separate hosts.  Below are the outputs from each host.  Any ideas what's going on?  Thanks in advance!

```

$ sudo aptitude install octave
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Note: selecting "octave3.0" instead of the
      virtual package "octave"
The following packages are BROKEN:
  octave3.0
The following packages have been automatically kept back:
  libtotem-plparser10
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 8825kB of archives. After unpacking 30.4MB will be used.
The following packages have unmet dependencies:
  octave3.0: Depends: libfftw3-3 but it is not installable
             Depends: libglpk0 (>= 4.25) but it is not installable
             Depends: libhdf5-serial-1.6.5-0 but it is not installable or
                      libhdf5-1.6.5-0 which is a virtual package.
             Depends: libqhull5 but it is not installable
             Depends: libsuitesparse-3.1.0 but it is not installable
             Depends: texinfo but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libatlas3gf-base [3.6.0-21.1ubuntu3 (hardy)]
libfftw3-3 [3.1.2-3ubuntu1 (hardy, now)]
libglpk0 [4.25-1 (hardy, now)]
libhdf5-serial-1.6.5-0 [1.6.5-5.2build1 (hardy)]
libqhull5 [2003.1-8 (hardy, now)]
libsuitesparse-3.1.0 [3.1.0-3 (hardy, now)]
texinfo [4.11.dfsg.1-4 (hardy, now)]

Score is -13

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

```

$ sudo aptitude install octave
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Note: selecting "octave3.0" instead of the
      virtual package "octave"
The following packages are BROKEN:
  octave3.0
The following packages have been automatically kept back:
  libglib2.0-dev libtotem-plparser10
The following packages have been kept back:
  gdm gtk2-engines-pixbuf libglib2.0-0 libgphoto2-2 libgphoto2-port0
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtk2.0-dev
  libnautilus-extension1 nautilus nautilus-data
0 packages upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 8647kB of archives. After unpacking 29.4MB will be used.
The following packages have unmet dependencies:
  octave3.0: Depends: libblas3gf but it is not installable or
                      libblas.so.3gf which is a virtual package. or
                      libatlas3gf-base but it is not installable
             Depends: libfftw3-3 but it is not installable
             Depends: libgfortran2 (>= 4.2.1) but it is not installable
             Depends: libglpk0 (>= 4.25) but it is not installable
             Depends: libhdf5-serial-1.6.5-0 but it is not installable or
                      libhdf5-1.6.5-0 which is a virtual package.
             Depends: liblapack3gf but it is not installable or
                      liblapack.so.3gf which is a virtual package. or
                      libatlas3gf-base but it is not installable
             Depends: libqhull5 but it is not installable
             Depends: libsuitesparse-3.1.0 but it is not installable
             Depends: texinfo but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libatlas3gf-base [3.6.0-21.1ubuntu3 (hardy)]
libfftw3-3 [3.1.2-3ubuntu1 (hardy)]
libgfortran2 [4.2.3-2ubuntu7 (hardy, now)]
libglpk0 [4.25-1 (hardy)]
libhdf5-serial-1.6.5-0 [1.6.5-5.2build1 (hardy)]
libqhull5 [2003.1-8 (hardy)]
libsuitesparse-3.1.0 [3.1.0-3 (hardy)]
texinfo [4.11.dfsg.1-4 (hardy)]

Score is -22

Accept this solution? [Y/n/q/?] n
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libatlas3gf-base [3.6.0-21.1ubuntu3 (hardy)]
libfftw3-3 [3.1.2-3ubuntu1 (hardy)]
libgfortran2 [4.2.3-2ubuntu7 (hardy, now)]
libglpk0 [4.25-1 (hardy)]
libhdf5-mpich-1.6.5-0 [1.6.5-5.2build1 (hardy)]
libqhull5 [2003.1-8 (hardy)]
libsuitesparse-3.1.0 [3.1.0-3 (hardy)]
texinfo [4.11.dfsg.1-4 (hardy)]

Score is -24

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```

---

### Post by mardawi on 2008-05-17
try
```
sudo apt-get autoclean
```
or
```
sudo apt-get clean
```
then try again

---


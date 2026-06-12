---
title: "NCL-install precompiled binary tar ball"
date: 2015-06-04
forum: General Help
---

### Post by whitney3 on 2015-06-04
Hello!

I am running Ubuntu 14.04.2 LTS 64-bit with gcc 4.8.2. Also, I am the only user on this machine. For my research, I need to use NCL. [http://www.ncl.ucar.edu/](http://www.ncl.ucar.edu/)

I used Ubuntu's software center to download the package. There are known bugs with this package due to wear the files are saved and where they should be saved. I was able to get around that issue but there are files missing from the package. NCL offers a precompiled binary tar ball to install. They do not offer one specifically for Ubuntu but suggest to use the Debian package and closest version of gcc which is the Debian 7.8 64-bit version with gcc 4.7.2. All of the options can be found here: [https://www.earthsystemgrid.org/dataset/ncl.630.html](https://www.earthsystemgrid.org/dataset/ncl.630.html)

When I save the tar ball in /home/whitney and try to extract it, I get this error: Could not create the hard link file:///home/whitney/ncl_ncarg-6.3.0.Linux_Debian7.8_x86_64_nodap_gcc472/bin/psplit

I have tried the OPeNDAP and non-OPeNDAP version and also the CENTOS version.

Help please!

---

### Post by steeldriver on 2015-06-04
Hello and welcome to the forums

How exactly are you trying to extract the gzipped tarball?

---

### Post by whitney3 on 2015-06-05
Thank you!

Right click and then extract here.

---

### Post by whitney3 on 2015-06-05
After doing a little reading, I now understand why I can't do a hard link in a directory. So I guess now my issue is where should I put the tarball and extract it?

---

### Post by steeldriver on 2015-06-05
Usually, I'd suggest creating a directory somewhere of your choosing in your home area, and unpacking it there first e.g. using the terminal

```

mkdir -p ~/ncl/ncl6.3.0

cd ~/ncl/ncl6.3.0

tar xvf ~/Downloads/ncl_ncarg-6.3.0.Linux_Debian7.8_x86_64_gcc472.tar.gz

```

assuming you downloaded the tarball to your Downloads directory. Once you see what's inside the archive, you can decide whether you need to move the contents to a system-level location, or whether you can simply run it from your home area.

Bear in mind that Ubuntu Trusty is really based on Debian 8 w/ gcc 4.8.2, so things may not work as expected

---

### Post by whitney3 on 2015-06-05
Okay so I was able to unpack it and move it to /usr/local/ncl6.3.0.

When I try to run the package now, it says it isn't installed.

The user manual for NCL says this:
In order to run NCL, you must set your NCARG_ROOT environment variable to the parent directory where the NCL executables and accompanying files were installed. You also need to make sure that the directory where the NCL executables reside is in your search path. It is best to do this from one of your .* files in your home directory. If you are not sure which shell you are running, you can do an "echo $SHELL".
If NCL resides in (say) /usr/local, the following setting would be appropriate:
From C-shell (csh):
setenv NCARG_ROOT /usr/local
setenv PATH $NCARG_ROOT:${PATH}
From bash, ksh:
export NCARG_ROOT=/usr/local
export PATH=/usr/local/bin:$PATH

I am not sure what I should change mine to. One of the lines from the code says load "$NCARG_ROOT/ncar/nclscripts/csm/gsn_code.ncl"

For me,the complete path is /usr/local/ncl6.3.0/lib/ncar/nclscripts/csm/gsn_code.ncl. So should NCARG_ROOT=/usr/local/ncl6.3.0/lib? 

If so, then what should PATH be because lib doesn't include a bin folder.

---

### Post by steeldriver on 2015-06-05
It should have unpacked a bin directory as well - so your exports would be

```

export NCARG_ROOT=$HOME/ncl/ncl6.3.0

export PATH=$HOME/ncl/ncl6.3.0/bin:$PATH

```

---

### Post by whitney3 on 2015-06-05
Alright that's done now but it still says ncl is not installed :(

---

### Post by whitney3 on 2015-06-05
I finally got it to work!!!!!!!!!! Thank you so much for your help!!!!!!!!!!!!!

---


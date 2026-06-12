---
title: "Problem installing TISEAN on Ubuntu 13.04"
date: 2014-03-18
forum: General Help
---

### Post by oevstaff on 2014-03-18
Hello everyone,

I am relatively new to Linux and I am currently trying to install an open source package TISEAN from [http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html](http://www.mpipks-dresden.mpg.de/~tisean/Tisean_3.0.1/index.html). I am running a Ubuntu 13.04. 

So I download the file, unzip and save it in the /usr/src directory. Then I enter the Tisean_3.0.1 directory and try to install it as the root user using the following commands

./configure --prefix=/usr/src/Tisean_3.0.1
make
checkinstall

./configure command does not flag up any problems. Then I run 'make' and 'checkinstall' and get a message saying that "the following programs could not be made/installed" listing all of the scripts in the Tisean_3.0.1 directory. Checkinstall finishes with "***failed to build the package".
P.S. I have tried 'make install' instead of 'checkinstall' too, but to no avail:(

I have no idea why this happens and I would really appreciate any help or strategies that others used to install TISEAN.

Thank you in advance for any help:)

---


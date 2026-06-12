---
title: "downgrade gdal package"
date: 2014-03-17
forum: General Help
---

### Post by dommer87 on 2014-03-17
Hello everybody!
I am using ubuntu12.04LTS but i need an old version of gdal library (geospatial data abstraction library for ubuntu10.04). The package to be downloaded via terminal is libgdal1-dev. The point is that by default ubuntu12.04 install gdal1.7.0 (1.7.3-6ubuntu3 version) while i need the gdal1.6.0 (according to [http://packages.ubuntu.com/lucid/allpackages](http://packages.ubuntu.com/lucid/allpackages) 1.6.3-3build2 version).
I tryed to manually downgrade the package after removing gdal1.7.0 and after doing sudo apt-get autoremove with:
**sudo apt-get install libgdal1-dev=1.6.3-3build2**.

Unfortunately the terminal says that can't find the versione1.6.3-3.build2 of the package libgdal1-dev. What's wrong? can anybody help me please? 

thanks very much!

---

### Post by monkeybrain20122 on 2014-03-17
It can't find it because there is no such package. The name is libgdal1-dev (not "libgdal1-dev=1.6.3-3build2") the version in the repo is 1.7
sudo apt-get install fetches the package with the correct name from the repository with whatever version that is in the repository. In this case it is Precise's repository and not Lucid's (and it is shut down already)

So the procedure to downgrade is: fetch the .deb from [http://packages.ubuntu.com/lucid/libgdal1-dev](http://packages.ubuntu.com/lucid/libgdal1-dev)
then right click to install it. Chances are it won't install because some of the dependencies cannot be met (since all are old versions)

If in the unlikely event that it installs, then open synaptic (if synaptic is not installed, sudo apt-get install synaptic), search for libgdal1-dev, highlight it and on the top bar click Packages and click 'Lock Version" that way it won't be upgraded.

Since it is not likely to install you should tell us exactly what program you need it for, there may be ways to work around it.

---


---
title: "Zenoss cannot install on Dapper!!!"
date: 2007-09-06
forum: General Help
---

### Post by psypher on 2007-09-06
I have been following the howtoforge instructions on installing zenoss but it will not compile. First I had an error which i fixed by running sudo apt-get install autoconf swig python-setuptools 
But now I am stuck and cannot find any info on how to fix it. Got the following error:

cp externallibs/setuptools*.egg build/simplejson-1.4
installing simplejson
make: *** [simplejson-install] Error 2
unable to build zenoss and prerequisites, see zenbuild.log

Did some googling and all I could come up with was that this is a python 2.5 issue. Well i'm not using python 2.5. dpkg -l python gives:

python          2.4.2-0ubuntu3

can anybody please help, this is quite urgent, it's thursday and i need this finished by monday

thanks

---

### Post by psypher on 2007-09-06
sorry forgot to mention I used zenoss-2.0.4-0.tar.gz to install (Iatest tarball)

---


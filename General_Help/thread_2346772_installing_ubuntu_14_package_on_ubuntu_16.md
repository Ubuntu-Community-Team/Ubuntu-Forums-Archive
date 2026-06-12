---
title: "installing ubuntu 14 package on ubuntu 16"
date: 2016-12-18
forum: General Help
---

### Post by jd872 on 2016-12-18
hi.
i am currently working on an project requring an old package.
mongodb-dev containing libmongoclient.a

this does not exist in ubuntu16.

i already tried backports.
i added:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
to
/etc/apt/sources.list
and run
sudo apt-get install -t xenial-backports mongodb-dev

but i got: "E: Unable to locate package mongodb-dev"

i also tried cloning "https://github.com/mongodb/mongo.git" and building it, but i only got 51GB of artifacts (and none was the required lib)

this is currently the one package stopping me from upgrading to ubuntu16.

does someone have an idea how i can get the package (it should be via cli, since it is on a remote machine)?

-joe

---

### Post by ian-weisser on 2016-12-18
Look at the 14.10 (Trusty) builds on [https://launchpad.net/ubuntu/+source/mongodb/](https://launchpad.net/ubuntu/+source/mongodb/)
By default, the list is collapsed - click the triangle to expand.

That will provide you the stable URL to wget the package from, then sudo dpkg -i /path/to/packagename.deb to install.

---


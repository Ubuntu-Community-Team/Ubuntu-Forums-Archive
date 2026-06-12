---
title: "Multi-arch package won't install for i386 dependency"
date: 2017-01-11
forum: General Help
---

### Post by ndeubert on 2017-01-11
I am running 16.04 amd64, but I have some development files that need to link with some 32bit python 2.7 libraries, so I have been trying to get them installed but keep getting stuck. The commands below should be self explanatory:

```
$sudo apt-get install python-protobuf:i386
...
The following packages have unmet dependencies:
 python-protobuf:i386 : Depends: python:i386 (< 2.8) but it is not going to be installed
                        Depends: python:i386 (>= 2.7~) but it is not going to be installed
                        Depends: python-pkg-resources:i386 but it is not installable
```

```
$ sudo apt-get install python2.7:i386
...
The following packages have unmet dependencies:
 python2.7:i386 : Depends: python2.7-minimal:i386 (= 2.7.12-1ubuntu0~16.04.1) but it is not going to be installed
```
```

$ sudo apt-get install python2.7-minimal:i386
```
(succeeded)

```
$ sudo apt-get install python2.7:i386 
```
(succeeded)

```
$ sudo apt-get install python-protobuf:i386
The following packages have unmet dependencies:
 python-protobuf:i386 : Depends: python-pkg-resources:i386 but it is not installable
```

But python-pkg-resources ([http://packages.ubuntu.com/xenial/python-pkg-resources](http://packages.ubuntu.com/xenial/python-pkg-resources)) is for all architectures so it should be happy to install it to satisfy the "i386" requirement shouldn't it? Is there a way to force it to appease the dependency?

---

### Post by dragonfly41 on 2017-01-11
I don't know too much about this package but I looked up to see if python-protobuf can be installed through anaconda.

[https://anaconda.org/anaconda/protobuf](https://anaconda.org/anaconda/protobuf)

This thread ...

[https://github.com/tensorflow/tensorflow/issues/1755](https://github.com/tensorflow/tensorflow/issues/1755)

suggests that ...

> Sorry for the late response. But yes, you need libprotobuf installed on your machine for the C++ extension in the python package to work. I will update the instructions to reflect that.


So perhaps you should check through Synaptic Package Manager if libprotobuf (which is a dependency for python-protobuf) is installed?

If you do decide to try anaconda or miniconda (I've only recently started using it) you should install the 64bit version.  This allows 32bit environments in addition to 64bit environments. Read its docs

---


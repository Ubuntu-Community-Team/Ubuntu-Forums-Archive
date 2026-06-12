---
title: "Installing dependencies in Ub 16.10"
date: 2017-06-10
forum: General Help
---

### Post by Semn on 2017-06-10
Hi, I am trying to install sage math on ubuntu 16.10, however I get this;

```
sudo apt-get install --no-install-recommends libboost-all-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adium-theme-ubuntu : Depends: python:any (< 2.8)
                      Depends: python:any (>= 2.7~)
 libboost-all-dev : Depends: libboost-dev but it is not going to be installed
                    Depends: libboost-tools-dev
                    Depends: libboost-atomic-dev but it is not going to be installed
                    Depends: libboost-chrono-dev but it is not going to be installed
                    Depends: libboost-context-dev but it is not going to be installed
                    Depends: libboost-coroutine-dev but it is not going to be installed
                    Depends: libboost-date-time-dev but it is not going to be installed
                    Depends: libboost-exception-dev but it is not going to be installed
                    Depends: libboost-filesystem-dev but it is not going to be installed
                    Depends: libboost-graph-dev but it is not going to be installed
                    Depends: libboost-graph-parallel-dev but it is not going to be installed
                    Depends: libboost-iostreams-dev but it is not going to be installed
                    Depends: libboost-locale-dev but it is not going to be installed
                    Depends: libboost-log-dev but it is not going to be installed
                    Depends: libboost-math-dev but it is not going to be installed
                    Depends: libboost-mpi-dev but it is not going to be installed
                    Depends: libboost-mpi-python-dev but it is not going to be installed
                    Depends: libboost-program-options-dev but it is not going to be installed
                    Depends: libboost-python-dev but it is not going to be installed
                    Depends: libboost-random-dev but it is not going to be installed
                    Depends: libboost-regex-dev but it is not going to be installed
                    Depends: libboost-serialization-dev but it is not going to be installed
                    Depends: libboost-signals-dev but it is not going to be installed
                    Depends: libboost-system-dev but it is not going to be installed
                    Depends: libboost-test-dev but it is not going to be installed
                    Depends: libboost-thread-dev but it is not going to be installed
                    Depends: libboost-timer-dev but it is not going to be installed
                    Depends: libboost-wave-dev but it is not going to be installed
 python-talloc : Depends: python:any (< 2.8)
                 Depends: python:any (>= 2.7~)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```



and

```
sudo apt-get -f install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 adium-theme-ubuntu : Depends: python:any (< 2.8)
                      Depends: python:any (>= 2.7~)
 libhdf5-serial-dev : Depends: libhdf5-dev but it is not going to be installed
 libopencv-dev : Depends: libopencv-core-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-ml-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-imgproc-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-video-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-objdetect-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-highgui-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-calib3d-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-flann-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-features2d-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-legacy-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-contrib-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-ts-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-photo-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-videostab-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-stitching-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-gpu-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-superres-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv-ocl-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv2.4-java (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libopencv2.4-jni (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libcv-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libhighgui-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Depends: libcvaux-dev (= 2.4.9.1+dfsg-2.1) but it is not going to be installed
                 Recommends: opencv-data but it is not going to be installed
 protobuf-compiler : Depends: libprotoc10 (= 3.0.0-7ubuntu3) but it is not going to be installed
 python-talloc : Depends: python:any (< 2.8)
                 Depends: python:any (>= 2.7~)
```



what can be done?

Would another ubuntu version be better for scientific gnu programs?

Thanks

---

### Post by oldos2er on 2017-06-10
The package sagemath is in the repositories, may I ask why you're installing a *-dev package? Are you intending to compile sagemath from source?

16.10 support ends next month, it's time to think about upgrading.

---

### Post by Semn on 2017-06-11
Thanks! I wanted to compile from source indeed.

About the Upgrade, I have tried, but no newer version than 16.10 are "catched" by the updating software. Can I try some more specific sudo command for this upgrade to 17.10 ?

Thank

---

### Post by oldos2er on 2017-06-11
I'm thinking you'd need to leave off the --no-install-recommends option, since that seems to be a problem. But why not simply do ```
sudo apt-get build-dep sagemath
```? 

Do you have Update Manager set to only notify you of LTS releases? Since 16.10 is not an LTS version, I'm not sure why this would be set. Something to check.

```
do-release-upgrade
``` would upgrade you to 17.04, ```
do-release-upgrade -d
``` would move you to 17.10, which is still in early development.

---

### Post by monkeybrain20122 on 2017-06-11
I have compiled sagemath in Ubuntu 16.04. Didn't have a problem except that it look forever.  It seems that you are having problem with protobuf. Did you upgrade your software with a ppa and then later disabled the ppa?

---

### Post by howefield on 2017-06-11
Moved to the "*General Help*" forum.

---

### Post by monkeybrain20122 on 2017-06-11
> **oldos2er said:**
> 

16.10 support ends next month, it's time to think about upgrading.

!7.04 also has only 9 month support. Instead of "upgrading" I would suggest downgrading and reinstalli 16.04. Especially since OP seems to like to compile stuffs, it wouldn't worth the trouble for the 9 month releases if you do a lot of compiling. 

Besides I won't suggest "do -release upgrade -d", it likely will break OP's system, judging from the fact that something fishy is already happening with his sources list, his is not a pristine system.

---

### Post by Semn on 2017-06-14
tried so:

~/Downloads$ sudo apt-get build-dep sagemath
[sudo] password for sem: 
Reading package lists... Done
E: You must put some 'source' URIs in your sources.list

---


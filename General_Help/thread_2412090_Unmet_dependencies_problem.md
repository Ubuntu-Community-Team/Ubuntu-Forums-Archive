---
title: "Unmet dependencies problem"
date: 2019-02-08
forum: General Help
---

### Post by tajiknomi on 2019-02-08
I have deleted cuda from my system which causes some dependency problems. Now when i try to install anything, i prompt with this error.


```
$ sudo apt-get install bc

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cuda-cudart-dev-10-0 : Depends: cuda-driver-dev-10-0 (>= 10.0.130) but it is not going to be installed
 cuda-libraries-dev-10-0 : Depends: cuda-driver-dev-10-0 (>= 10.0.130) but it is not going to be installed
 cuda-samples-10-0 : Depends: cuda-driver-dev-10-0 but it is not going to be installed
 cuda-toolkit-10-0 : Depends: cuda-nvml-dev-10-0 (>= 10.0.130) but it is not going to be installed
 cuda-visual-tools-10-0 : Depends: cuda-driver-dev-10-0 (>= 10.0.130) but it is not going to be installed
                          Depends: cuda-nvml-dev-10-0 (>= 10.0.130) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)
```

I also tried apt-get -f install

```
$ sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  cuda-driver-dev-10-0 cuda-nvml-dev-10-0
The following NEW packages will be installed:
  cuda-driver-dev-10-0 cuda-nvml-dev-10-0
0 upgraded, 2 newly installed, 0 to remove and 189 not upgraded.
10 not fully installed or removed.
Need to get 0 B/63.5 kB of archives.
After this operation, 556 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 file:/var/cuda-repo-10-0-local-10.0.130-410.48  cuda-driver-dev-10-0 10.0.130-1 [12.0 kB]
Get:2 file:/var/cuda-repo-10-0-local-10.0.130-410.48  cuda-nvml-dev-10-0 10.0.130-1 [51.6 kB]
(Reading database ... 123484 files and directories currently installed.)
Preparing to unpack .../cuda-driver-dev-10-0_10.0.130-1_amd64.deb ...
Unpacking cuda-driver-dev-10-0 (10.0.130-1) ...
dpkg: error processing archive /var/cuda-repo-10-0-local-10.0.130-410.48/./cuda-driver-dev-10-0_10.0.130-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-10.0/lib64', which is also in package cuda-npp-10-0 10.0.130-1
Preparing to unpack .../cuda-nvml-dev-10-0_10.0.130-1_amd64.deb ...
Unpacking cuda-nvml-dev-10-0 (10.0.130-1) ...
dpkg: error processing archive /var/cuda-repo-10-0-local-10.0.130-410.48/./cuda-nvml-dev-10-0_10.0.130-1_amd64.deb (--unpack):
 trying to overwrite '/usr/local/cuda-10.0/lib64', which is also in package cuda-npp-10-0 10.0.130-1
Errors were encountered while processing:
 /var/cuda-repo-10-0-local-10.0.130-410.48/./cuda-driver-dev-10-0_10.0.130-1_amd64.deb
 /var/cuda-repo-10-0-local-10.0.130-410.48/./cuda-nvml-dev-10-0_10.0.130-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

1) I want to get rid all the files related to cuda (safely)
2) Get rid of the above dependecy error

Any help would be appreciated. thanks

---

### Post by Claus7 on 2019-02-08
Hello,

from the last 4 lines of your output it seems that you have added a repository that is related with cuda. First I think that you should remove it, reload repositories and purge all cuda files and then proceed. 

You could try also removing the last two packages with sudo apt remove and then remove the repositories. Which are the messages that you are getting with these steps?

Regards!

---

### Post by tajiknomi on 2019-02-08
Hi !

Removed the repositories related to cuda in /etc/apt/sources.list.d/cuda*

Purged the cuda related files 

> $ sudo apt-get --purge remove cuda*

Solved.

Thankyou Claus7 :)

---


---
title: "gstreamer0.8-plugins cannot install"
date: 2005-06-13
forum: General Help
---

### Post by nmarmol on 2005-06-13
Hi,

I trying to install codecs following the instruction at ubutunguide.org.

But, when execute command 

**********************************
$ sudo apt-get install gstreamer0.8-plugins, I received the following message:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-plugins: Depends: gstreamer0.8-a52dec but it is not going to be i
nstalled
                        Depends: gstreamer0.8-aa but it is not installable
                        Depends: gstreamer0.8-artsd but it is not installable
                        Depends: gstreamer0.8-caca but it is not installable
                        Depends: gstreamer0.8-festival but it is not installable
                        Depends: gstreamer0.8-jack but it is not installable
                        Depends: gstreamer0.8-mad but it is not going to be inst
alled
                        Depends: gstreamer0.8-mikmod but it is not installable
                        Depends: gstreamer0.8-mpeg2dec but it is not going to be
 installed
                        Depends: gstreamer0.8-sid but it is not installable
                        Depends: gstreamer0.8-swfdec but it is not going to be i
nstalled
E: Broken packages
**********************************

What can I do?
anny Suggesstion?

Regards
nelson

---

### Post by GrumpySmurf on 2005-06-14
Usually the messages you're seeing indicate that apt is unable to find the dependencies in the repository.  Did you follow the repository instructions at the beginning of the guide?  What are your /etc/apt/sources.list contents (without comments or whitespace):

```
$ egrep -v "^#|^$" /etc/apt/sources.list
```

---


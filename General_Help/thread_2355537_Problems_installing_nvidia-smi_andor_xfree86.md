---
title: "Problems installing nvidia-smi and/or xfree86"
date: 2017-03-13
forum: General Help
---

### Post by orthoducks on 2017-03-13
I'm trying to install nvidia-smi on my Ubuntu system (16.04). On an earlier installation I was able to do this simply by running 'sudo apt-get install nvidia-smi'. When I do that now, I get the messages:

```
E: Could not get lock /v ar/lib/dpkg/loc - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
Probably not. I just rebooted the system after installing the driver (selecting “NVIDIA binary driver version 340.101” from Additional Drivers). I have not started any other applications.

I looked for alternate installation instructions and found a process that involves installing NVIDIA drivers with an NVIDIA run file. It requires xfree86 as a prerequisite, and when I try to install that (sudo apt-get install xserver-xfree86) I got these messages:

```
Package xserver-xfree86 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package 'xserver-xfree86' has no installation candidate.
```
This is not helping. Can someone give me advice please: How can I get around either of the problems I encountered, or install nvidia-smi by another (hopefully simple) process?

---


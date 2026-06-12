---
title: "Boot Partition is Full"
date: 2016-02-27
forum: General Help
---

### Post by jrh2 on 2016-02-27
I have been trying to install openssh-server, on my Ubuntu server, with apt-get. Whenever I try to use apt-get I get the following error: E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). The following packages have unmet dependencies: ... it then proceeds to list a bunch of Linux kernels. I have been told a solution to this is to purge all of the old kernels with apt-get but every time i try this I get the same error. What is the problem here? Why cant i install any new software with apt-get? I'm a bit of an Ubuntu n00b so I might be leaving something important out, any help is appreciated.

---

### Post by yancek on 2016-02-27
The problem apparently, is that you have a separate boot partition and you haven't cleaned it up or it's too small.  A number of systems I use never seem to have more than two kernels as in updates, older ones are removed.  This apparently doesn't happen with Ubuntu.

> Try 'apt-get -f install'  

What happened when you tried the above suggestion?

> every time i try this I get the same error

What is the exact command you use to try to remove kernels?  You forgot to post the actual error.

> Why cant i install any new software with apt-get?

You probably could if you de-selected the new kernel.  The link below is the official Ubuntu documentation on removing old kernels.

  [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels)

---


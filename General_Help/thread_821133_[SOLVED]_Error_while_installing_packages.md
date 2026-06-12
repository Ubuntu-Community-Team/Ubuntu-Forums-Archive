---
title: "[SOLVED] Error while installing packages"
date: 2008-06-06
forum: General Help
---

### Post by raylistic87 on 2008-06-06
I keep having this error when i want to install packages.

Error : wrong architecture 'i386'

Is there a bug somewhere? Cause i seriously think mine is the i386.

I am trying to install adobe reader and skype for ubuntu.

And i have type uname -m and this is the result:

Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

Thanks for the help provided. You guys have been really helpful!:KS

---

### Post by drs305 on 2008-06-06
> **raylistic87 said:**
> I keep having this error when i want to install packages.

Error : wrong architecture 'i386'

Is there a bug somewhere? Cause i seriously think mine is the i386.

I am trying to install adobe reader and skype for ubuntu.

And i have type uname -m and this is the result:

Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

Thanks for the help provided. You guys have been really helpful!:KS


This line indicates you are running a 64-bit machine:
```

Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 **x86_64** GNU/Linux

```

There is an entry in synaptic for acroread, which is adobe acrobat. The good news is that anything listed in the synaptic repositories is the correct version (will run in 64 bit) for your machine. You can simply install **acroread** and will have the proper adobe acrobat for your machine.

skype is also listed in the 64-bit repository. I don't use it but it's listed in synaptic so it will run. It looks like you are in luck for both apps ;-)

---

### Post by raylistic87 on 2008-06-06
How do i access that repository to install these packages?

---

### Post by drs305 on 2008-06-06
They are both in the medibuntu repositories. To add them (for hardy):

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

After that you should see acroread and skype and see the new medibuntu repository in the synaptic  Settings > Repositories > Third-party tab.

If you have problems installing or running these apps, posts should normally be placed in the 64-bit forum:
[http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

And if this answers your questions please mark this solved: Thread tools at top right of first post.

---

### Post by raylistic87 on 2008-06-07
thanks alot! I got it!

---


---
title: "Install older linux headers"
date: 2013-05-07
forum: General Help
---

### Post by Finalfantasykid on 2013-05-07
I've been having some issues with my upgrade to 13.04 (occasional no sound on boot, problems with restarting, and occasional lack of resume from suspend), and so I'm pretty sure it is kernel related.  I still have the 3.5 kernel installed from 12.10 and I can boot fine with it, but it seems like I am missing the kernel headers since when I run **sudo dkms autoinstall** the output is:

```
Error! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.5.0-27-generic cannot be found.
Please install the linux-headers-3.5.0-27-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located

```

Also is there anyway that I can still get updates for 3.5 kernel, maybe through a ppa or something.  The issues I am having will hopefully get fixed with an update at some point, but until then I'll be using the 3.5 kernel and would like to still receive updates.

---

### Post by CharlesA on 2013-05-07
```
sudo apt-get install linux-headers-3.5.0-27-generic
```

Doesn't work?

---

### Post by Finalfantasykid on 2013-05-07
I get the following:

```
E: Unable to locate package linux-headers-3.5.0-27-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-27-generic
```

What about this? [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.11-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5.7.11-quantal/)

Or how about this ppa [https://launchpad.net/~kernel-ppa/+archive/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/pre-proposed)

---

### Post by CharlesA on 2013-05-07
Not sure, but I know I wouldn't use a pre-proposed kernel.

If those 3.5 kernels are from 12.10 and you have your sources set for 13.04, that is probably why they can't find the headers package.

---

### Post by Finalfantasykid on 2013-05-07
What if I add the following to my sources.list?

```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main
```

Would that totally mess up my repository?

---

### Post by CharlesA on 2013-05-07
Don't know for sure, but probably.

---

### Post by Finalfantasykid on 2013-05-08
Well I gave it a shot, and surprisingly it worked fine with no errors.  I was able to get the headers installed, and now bumblebee is working :)

---

### Post by CharlesA on 2013-05-08
Awesome. :)

---


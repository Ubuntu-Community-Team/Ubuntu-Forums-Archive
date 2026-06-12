---
title: "Execute flag -a"
date: 2015-07-18
forum: General Help
---

### Post by ngdias2 on 2015-07-18
I'm reading a guide that includes instalation of Nvidia graphic drivers with a -a flag, like this:

> sudo ./NVIDIA-Linux-x86_64-343.22.run -a

I Googled the best I could but was unable to find an explanation for the -a flag. Better yet, I'd like to see a list of possible flags and their effect.

Could someone point me in the right direction, please?
Thanks!

---

### Post by Keith_Helms on 2015-07-19
No idea where they got this information, but look here:

[http://www.manpages.spotlynx.com/gnu_linux/man/nvidia-installer.1](http://www.manpages.spotlynx.com/gnu_linux/man/nvidia-installer.1)

---

### Post by oldos2er on 2015-07-19
If you're new to Ubuntu (or even if you're not) it's best to install Nvidia drivers from the repositories. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA_drivers_provided_by_the_Ubuntu_repositories](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#NVIDIA_drivers_provided_by_the_Ubuntu_repositories)

---

### Post by steeldriver on 2015-07-19
I agree with the advice already given - stick to the official versions unless you really know what you're doing

However, for the record, you can get a list of all the installer options by running it in help mode: either

```

./NVIDIA-Linux-x86_64-343.22.run --help

```
or (short form)
```

./NVIDIA-Linux-x86_64-343.22.run -h

```

You should see that
```

  -a, --accept-license
      Bypass the display and prompting for acceptance of the
      NVIDIA Software License Agreement.  By passing this option
      to nvidia-installer, you indicate that you have read and
      accept the License Agreement contained in the file
      'LICENSE' (in the top level directory of the driver
      package).

```

---


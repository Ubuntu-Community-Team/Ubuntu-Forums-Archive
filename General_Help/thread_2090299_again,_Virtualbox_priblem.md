---
title: "again, Virtualbox priblem"
date: 2012-12-01
forum: General Help
---

### Post by keter682 on 2012-12-01
[http://ubuntuforums.org/showthread.php?t=2088833](http://ubuntuforums.org/showthread.php?t=2088833)

After another system update problem return :( 
but  /etc/init.d/vboxdrv setup create log-file 
> DKMS: add completed.
Failed to install using DKMS, attempting to install without
Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.

---

### Post by SeijiSensei on 2012-12-02
The VirtualBox installer needs to compile a custom "kernel module" that matches your installed Linux kernel.  In order to do this there needs to be some files on your system that contains information required for this compilation.  These are called "kernel-headers" in Ubuntu.  If you are comfortable with the command prompt, try this.  First run the command "uname -a" and you will get the current kernel version like this:

```
Linux [hostname] 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

(The [hostname] field will report the name of your computer.)  This result tells me I'm running kernel 3.2.0-33-generic.  To install the matching headers, run the commands:

```

sudo apt-get update
sudo apt-get install kernel-headers-3....

```

replacing 3.... with the matching kernel version from before.  On my system, I'd install "kernel-headers-3.2.0-33-generic".

---

### Post by keter682 on 2012-12-02
it's works. I'm hope that it's never repeat.

---

### Post by SeijiSensei on 2012-12-02
Now that you've installed the headers once, they will be updated along with the kernel if a new version is released.

---

### Post by Cheesemill on 2012-12-02
Just to add, you can make the steps that SeijiSenei outlined above into one command by doing:
```
sudo apt-get install linux-headers-`uname -r`
```

---


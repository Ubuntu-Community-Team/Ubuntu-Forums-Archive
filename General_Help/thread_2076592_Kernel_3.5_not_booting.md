---
title: "Kernel 3.5 not booting"
date: 2012-10-26
forum: General Help
---

### Post by Fibonacci on 2012-10-26
Hello.

I recently upgraded to 12.10, but I'm stuck on kernel 3.2.0-32. When booting the newest kernel I get only this on my screen:

Loading Linux 3.5.0-17-generic...
Loading initial ramdisk...

And my computer is completely stuck at that point. The only way to make it respond is to forcefully power it off and on again.
I read on this forum that 3.5.0-17 was buggy and I should try 3.5.0-18 from quantal-proposed. The result, however, was exactly the same:

Loading Linux 3.5.0-18-generic...
Loading initial ramdisk...

And stuck again.
Recovery mode on both kernels, though, is working fine.

Is there any way I can make the new kernels boot, or am I stuck on 3.2.0-32 for the time being?

---

### Post by dino99 on 2012-10-26
i would suggest to check dkms installation and watch the logs to finf usefull warnings/errors. Whats happen when you try booting 3.5 in recovery mode then select "repair package"

---

### Post by Fibonacci on 2012-10-26
> **dino99 said:**
> i would suggest to check dkms installation
It is installed, with no errors.
> **dino99 said:**
> and watch the logs to finf usefull warnings/errors.
Which logs?
> **dino99 said:**
> Whats happen when you try booting 3.5 in recovery mode then select "repair package"
It prints "/dev/sda3: clean, ##/## files, ##/## blocks" and then does nothing until I press Ctrl+Alt+Del, at which point it reboots.

---

### Post by Fibonacci on 2012-10-27
Bump.

---

### Post by Fibonacci on 2012-10-29
Bump.

---

### Post by pqwoerituytrueiwoq on 2012-10-29
```
sudo apt-get install linux
```does that give you any errors?
you can try the 3.6.3 kernel (installer attached)

---

### Post by Fibonacci on 2012-10-29
> **pqwoerituytrueiwoq said:**
> ```
sudo apt-get install linux
```does that give you any errors?
Not at all.
> **pqwoerituytrueiwoq said:**
> you can try the 3.6.3 kernel (installer attached)
How do I use it?

---

### Post by pqwoerituytrueiwoq on 2012-10-29
there is a install script (named install) in the archive, run that in a terminal
What do these command give you
```
readlink /initrd.img
readlink /initrd.img.old
readlink /vmlinuz
readlink /vmlinuz.old
```

---

### Post by Fibonacci on 2012-10-29
> **pqwoerituytrueiwoq said:**
> there is a install script (named install) in the archive, run that in a terminal
What do these command give you
```
readlink /initrd.img
readlink /initrd.img.old
readlink /vmlinuz
readlink /vmlinuz.old
```

```
$ readlink /initrd.img
boot/initrd.img-3.5.0-18-generic
$ readlink /initrd.img.old
/boot/initrd.img-3.5.0-18-generic
$ readlink /vmlinuz
boot/vmlinuz-3.5.0-18-generic
$ readlink /vmlinuz.old
boot/vmlinuz-3.5.0-18-generic

```

---

### Post by Fibonacci on 2012-11-01
Bump.

---

### Post by Fibonacci on 2012-11-05
Bump.

---

### Post by Fibonacci on 2012-11-06
Bump.

---

### Post by pqwoerituytrueiwoq on 2012-11-06
did the 3.6 kernel not work either? have you tried booting with nomodeset?

---

### Post by Fibonacci on 2012-11-08
> **pqwoerituytrueiwoq said:**
> did the 3.6 kernel not work either?
No, I get the following error on the installer:
```
Need a couple dependencies
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cli is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
You did not install the dependencies
```
> **pqwoerituytrueiwoq said:**
> have you tried booting with nomodeset?
That makes it *boot*, but the desktop is unusable: I have no cursor, the maximum possible screen resolution is too small, and the colours look terrible.
I couldn't include a screenshot because, while the display is bad, the screenshots for some reason are taken as if everything were normal.

---

### Post by Fibonacci on 2012-11-10
Bump.

---

### Post by Fibonacci on 2012-11-11
Bump.

---

### Post by Fibonacci on 2012-11-15
Bump.

---

### Post by Fibonacci on 2012-11-24
Bump.

---

### Post by Fibonacci on 2012-12-02
Bump.

---

### Post by Fibonacci on 2012-12-03
Update:

I installed kernel 3.6 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-quantal/).
It has the same problems as the previous versions, but at least, when booting with nomodeset, the colours look fine and the desktop is partly usable.

What else can I try?

---


---
title: "DMESG do you see any errors?"
date: 2014-09-29
forum: General Help
---

### Post by robin_de_bruin on 2014-09-29
hey please all take a look at this file [http://pastebin.com/Lp84vzWs](http://pastebin.com/Lp84vzWs)

---

### Post by nerdtron on 2014-09-29
It's a bit long to read, are you having specific problems so that we can filter out the log?

---

### Post by oldos2er on 2014-09-29
> **robin_de_bruin said:**
> hey please all take a look at this file [http://pastebin.com/Lp84vzWs](http://pastebin.com/Lp84vzWs)

Please read [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

The more background information you can give regarding your problem will aid others trying to help you.

---

### Post by tgalati4 on 2014-09-29
Buffer I/O errors are not good.  What device is sr0?  A CDROM perhaps?  Are you running from a LiveDVD?

Open a terminal:

```
sudo fdisk -l
```

and

```
hostname
```

If the hostname above does not match what you have in /etc/hosts, then you will get hostname errors.

Everything else looks fine.

---

### Post by robin_de_bruin on 2014-09-30
ok it doesnt show GRUB only a flashing _
in the top left corner

---

### Post by tgalati4 on 2014-09-30
Is it possible that GRUB went directly to boot and the boot failed?  Try rebooting (power-off then power-on) and hit "Esc" or "Alt-F1" and describe what it says.  What is the make and model of this system?  Have you installed Ubuntu to the hard drive or are you booting from a USB stick?

---

### Post by robin_de_bruin on 2014-09-30
installed to 1 and only HDD here is video of it [http://youtu.be/kgVNpiTbtz8](http://youtu.be/kgVNpiTbtz8)

---

### Post by tgalati4 on 2014-09-30
That looks like a Kernel Mode Setting (KMS) problem.  There is a framework called *plymouth* that controls what happens with graphics during boot.  When that doesn't work, you get a blank screen (and a flashing cursor) in your case.

Your system boots OK otherwise and you are able to log into it and use it normally--Correct?

You can turn off kms using the *nomodeset* switch during boot:  [http://askubuntu.com/questions/207175/what-does-nomodeset-do](http://askubuntu.com/questions/207175/what-does-nomodeset-do)

Plymouth has been known to cause some problems for certain computers/graphics cards:  [http://askubuntu.com/questions/tagged/plymouth](http://askubuntu.com/questions/tagged/plymouth)

Is this machine dual-boot?  Windows and Ubuntu?  If not, then stay logged into Ubuntu all the time and just put the computer to sleep.  No more bootup weirdness.

---

### Post by robin_de_bruin on 2014-09-30
still the same here is my grub config
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

---

### Post by tgalati4 on 2014-09-30
Did you perform the following?

```
sudo update-grub
```

Otherwise the changes don't take effect.

What is your graphics card?

```
lspci | grep VGA
```

Try a few more changes.  Take notes on what you changed:

> 
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=20
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset splash"
GRUB_CMDLINE_LINUX=""


---

### Post by robin_de_bruin on 2014-09-30
lscpi | grep VGA
gives this 
```
output 02:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300 GE] (rev a1)

```

and yes i ran update grub command


and i changed my grub to the one you posted
now i gives a fast rolling lines 

Video coming soon

---

### Post by robin_de_bruin on 2014-09-30
never mind altho thanks for helping me i will revert  to original setting i now
got an error at startup 
about upstart error power


to scared and it works
so (
don't fix what ain't broke :) )


however maybe im little further
[https://www.youtube.com/watch?v=CIlZTLS14LU&feature=youtu.be](https://www.youtube.com/watch?v=CIlZTLS14LU&feature=youtu.be)


new grub 
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=10
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by tgalati4 on 2014-10-01
The scrolling text can be paused using the Pause/Break key on your keyboard.  It is helpful to see what is going on.  Once everything is fixed, then you use the "quiet" setting to hide the messages.  You can't fix what you can't see.

Hit "Esc" during the countdown and that should take you to the GRUB menu.  You can also do some troubleshooting from there as well.

Your bootup looks OK.  Did you have a second monitor hooked up to a laptop?  If so, then that might explain the flickering cursor in the upper right corner.

With some dual-monitor setups, that is normal.

---

### Post by robin_de_bruin on 2014-10-01
is it bad if i cant use grub cause the PC works ok ??

---

### Post by tgalati4 on 2014-10-01
Does GRUB2 not come up during the countdown when you hit "Escape" key?  I forgot, you only have one operating system installed (Ubuntu) so by default, GRUB2 will not display a menu.  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by robin_de_bruin on 2014-10-01
yes it does :)
is that good or bad ?

it think will mark this as solved then :D

---

### Post by robin_de_bruin on 2014-10-01
no i dont this is a desktop computer

as to the question if i have 2 monitors connected

---


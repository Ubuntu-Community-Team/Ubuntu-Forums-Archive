---
title: "Ndisrapper doesn't exists?"
date: 2007-02-28
forum: General Help
---

### Post by lsutiger on 2007-02-28
I am in the process of trying to get my Broadcom BCM43xx wireless card to work on my Acer Travelmate Aspire 3000 notebook.

I have the bcm4318.all.tar.gz file on the desktop.
I ran this code
```
cd ~/Desktop
tar -xf bcm4318*.tar.gz
sudo ./ndiswrapper_setup

```
Here's the output:

./ndiswrapper_setup: command substitution: line 44: unexpected EOF while looking for matching `"'
./ndiswrapper_setup: command substitution: line 45: syntax error: unexpected end of file
./ndiswrapper_setup: command substitution: line 44: unexpected EOF while looking for matching `"'
./ndiswrapper_setup: command substitution: line 45: syntax error: unexpected end of file
Dapper final release detected.
Installing ndiswrapper-utils...
Done...
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
You appear to have an i386 system...installing the i386 drivers...
Done...
Adding drivers to ndiswrapper...
Done...
Gathering wireless card information...
Done...

??? I have no idea what to do.

---

### Post by zanglang on 2007-03-01
Try typing this in a console:
```
ndiswrapper -l
```
Does that show anything?

Alternatively, you can try this thread:
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by lsutiger on 2007-03-07
```
complexity@complexity-laptop:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

```

---

### Post by zanglang on 2007-03-08
That means the script did not install your drivers correctly, although it *did* manage to install ndiswrapper from the repository.

Try the guide given in my link earlier.

---


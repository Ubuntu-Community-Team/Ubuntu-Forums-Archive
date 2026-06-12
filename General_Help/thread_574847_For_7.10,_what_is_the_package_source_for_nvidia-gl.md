---
title: "For 7.10, what is the package source for nvidia-glx-new?"
date: 2007-10-13
forum: General Help
---

### Post by ehdtkqorl123 on 2007-10-13
I just installed unstable gutsy.

As I know, compiz-fusion is installed in it by deafult.

But when I tried to enable nvidia accelerated graphics driver, it says 

The software source for the package nvidia-glx-new is not enabled.

So I tried to use

sudo apt-get install nvidia-glx-new 

but then it says

Package nvidia-glx-new is not available but is refferred by another package. blah...

What should I do? Any help is appreciated.

FYI, when i go to sources.list, all lines  are commented out by installer cuz it failed to verify things..

---

### Post by Pumalite on 2007-10-13
What video card do you have?

---

### Post by ehdtkqorl123 on 2007-10-13
256MB NVIDIA GeForce 8500GT

this..

---

### Post by Pumalite on 2007-10-13
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

 when grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver

---

### Post by ehdtkqorl123 on 2007-10-13
I got it working! thanks !

---

### Post by Pumalite on 2007-10-13
You are welcome. Good luck.

---


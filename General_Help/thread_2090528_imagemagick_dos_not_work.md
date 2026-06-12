---
title: "imagemagick dos not work"
date: 2012-12-02
forum: General Help
---

### Post by cazz on 2012-12-02
Hi
I have install imagemagick but it does not run

When I'm in the terminal and write

"convert" it just say "Command not found"

---

### Post by Cheesehead on 2012-12-02
Usually that means imagemagic is not installed, or has been broken and needs to be reinstalled.

Test: Is imagmagick installed?  Here is how to check.

If imagemagick is not installed, the test will have no output. Go ahead and install imagemagick.
```
system:~$ dpkg --get-selections | grep imagemagick
system:~$ sudo apt-get install imagemagick

```

If imagemagick is installed but broken, the test will show imagemagick installed. reinstall it:
```
system:~$ dpkg --get-selections | grep imagemagick
imagemagick					install
imagemagick-common				install
imagemagick-doc					install
system:~$ sudo apt-get install --reinstall imagemagick
```

---

### Post by cazz on 2012-12-03
Hi
Yes you was right, it was not install.

Strange I did guess that I have it install but it was not.

So now it is up and running :)

---


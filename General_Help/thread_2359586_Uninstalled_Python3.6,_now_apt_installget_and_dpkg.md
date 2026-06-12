---
title: "Uninstalled Python3.6, now apt install/get/ and dpkg errors"
date: 2017-04-25
forum: General Help
---

### Post by crunki on 2017-04-25
Running ubuntu 16.10.

I removed Python3.6 (I had 3.5 and didn't want 3.6) and now I get dpkg and apt errors all over the place. Can't even do lsb_release -a without getting -bash: /usr/bin/lsb_release: /usr/bin/python3: bad interpreter: Too many levels of symbolic links.

If I try to for example (re)install Python3 (or do anything with apt for that matter) I get the following:[https://pastebin.com/im1bxc1R](https://pastebin.com/im1bxc1R)
I've tried (re)installing various Python versions, and the packages shown at the end of the pastebin.
I've even tried to manually download and install Python3.6, but when I run the last command sudo make install I get this at the end: [https://pastebin.com/DYynaiKe](https://pastebin.com/DYynaiKe)
Thanks in advanced, and please help :(

The original Python3.6 was installed by the following:
>sudo add-apt-repository ppa:fkrull/deadsnakes 
>sudo apt-get update
>sudo apt-get install python3.6

The manual download/install (after the problems began):
>wget [https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tar.xz](https://www.python.org/ftp/python/3.6.1/Python-3.6.1.tar.xz)
>tar xJf ./Python-3.6.1.tar.xz
>cd ./Python-3.6.1
>./configure 
>make && sudo make install

---

### Post by oldfred on 2017-04-25
Post this:
ls -l /usr/bin/python*

Looking to see why this, you may have a link to a link?
Too many levels of symbolic links.

Generally you do not uninstall the default python(s). System runs on those and without them or even wrong version system is then broken.
It used to be that only recourse was total new install, but now you can normally do a few things and maybe repair it.

---


---
title: "Bash script Dependencies"
date: 2014-01-11
forum: General Help
---

### Post by jozamm on 2014-01-11
Hi all,

I am in the process of install a 3rd party program. (Altera Quartus Free Edition). The installation file is in the form of a large script (.sh) which than launches a GUI. While installing it will stop and ask for a particular library which I will download manually, start the installation again and wait for it to stop asking for the next package. This happened when I was testing the program on a virtual machine (I forgot which libraries were requested, and this issue may crop up again in the future), now I am going to install on actual installation.

Is there way I can extract these dependencies beforehand, install the libraries so the installation would be smooth?

Thanks,

Regards,

Joseph

---

### Post by CharlesA on 2014-01-11
You would need to find out what package the commands it is trying to run are and check the dependencies for each package.

Might want to check here, though:
[http://chehsunliu.wordpress.com/2013/01/15/install-altera-quartus-12-1-in-ubuntu-12-04/](http://chehsunliu.wordpress.com/2013/01/15/install-altera-quartus-12-1-in-ubuntu-12-04/)

---

### Post by pbrane on 2014-01-11
Some large install scripts have a shell script portion and a binary portion. If you want to see the shell script portion of file you can open it in a hex editor (e.g., ghex) and copy/paste that portion to a text editor. You'll probably have to reformat it to read it easily.

---


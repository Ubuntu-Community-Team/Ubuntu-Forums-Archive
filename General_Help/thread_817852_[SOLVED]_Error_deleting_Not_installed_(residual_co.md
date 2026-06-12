---
title: "[SOLVED] Error deleting Not installed (residual config) package"
date: 2008-06-04
forum: General Help
---

### Post by leetrefz on 2008-06-04
Clearing my 'Not installed (residual config)' list in Synaptic, I get this error message:

E: linux-ubuntu-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1

Anyway to get rid of it? hate useless stuff on my drive. 
thx!

---

### Post by kaibob on 2008-06-04
I had a similar problem and the solution was to create an empty directory as follows:

/lib/modules/2.6.22-14-generic

Synaptic then worked fine.

---

### Post by iaculallad on 2008-06-04
Try executing the commands:

```
sudo apt-get autoclean
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by leetrefz on 2008-06-04
creating the directory worked. thanks!

---

### Post by Euphorion on 2008-06-21
Hallo

I have read the How To's and threads concerning the removal of unwanted Linux Kernels and the modification of Grub. I adopted to use the synaptic approach using the graphical package manager in System -> Administration and apparently all went well. I had in mind the Post from leetrefz concerning the error message about the non removal of /lib/modules/2.6.22-14-generic. Creating an empty directory is as far as I can ascertain not the real solution.

What Synaptics cannot do, is to remove the  /lib/modules/2.6.22-xx-generic because it is not empty. Whereby xx refers to the version that was to be removed. This directory contains many sub-directories containing links. If I try to remove these, I cannot because I have no permission to do so (from Gnome file manager). The only other thing that I can think of is to remove these directory trees from a terminal having administrator rights, a tedious task owing to the sheer number. The other thing would be to start a file manager with administration rights.

The only thing which bothers me, if synaptics is not allowed to, or cannot remove these directories, is it prudent to remove them at all?

I have also tryed the commands recommended by iaculallad in his post:

Sudo apt-get autoclean
sudo deborphan | xargs sudo apt-get -y remove --purge

In Hardy deborphan must be installed via synaptics and I noticed that there is a graphical version of deborphan, running this and inspecting the results do not seem to indicate that the /lib/modules will be removed.

Is it possible to uninstall the modules seperatley and if so how? Under what names can they be found in synaptic? Any Ideas

Thanks in advance

---


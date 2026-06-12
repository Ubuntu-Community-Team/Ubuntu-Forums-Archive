---
title: "Grub2: Problem with /etc/grub.d/05_debian_theme preventing updates"
date: 2014-12-06
forum: General Help
---

### Post by Katzwinkel on 2014-12-06
Hi,
for quite some time now I have been unable to update my xubuntu system or install new software via the software center.
Everytime the process hangs at the step "Grub-configuration file is beeing generated". Then it does nothing until i hit enter on the console, at which point I get this error message:

```
/etc/grub.d/05_debian_theme: 143: /etc/grub.d/05_debian_theme: Syntax error: "done" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-33-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
```

what can I do? Should I purge and reinstall grub? How would I do that?

I already got the adIvice that I should delete all obsolete kernels. However, when I try to do this I run into the exact same problem: Process hangs at the Grub-configuration file generation and then yields th above error message

---

### Post by fantab on 2014-12-06
The problem seems to with *linux-image-3.13.0-33-generic*, you have to remove it. If you have 'Synaptic Package Manager' installed then use it to remove it or:

```
$ sudo -i
# dpkg --purge linux-image-3.13.0-33-generic    
# apt-get remove --purge linux-image-3.13.0-33-generic    
# apt-get clean
# apt-get dist-upgrade
# exit
```

But before you run the above set find out what kernel you are using with:
```
sudo uname -r
```
and confirm that you won't be removing the same kernel you are using.

If you see any errors after running the code 'apt-get dist-upgrade' then post he errors here.

---


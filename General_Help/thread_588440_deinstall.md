---
title: "deinstall"
date: 2007-10-23
forum: General Help
---

### Post by johndela1 on 2007-10-23
I have removed a package with apt-get remove pkgname, but it still shows up here:

jgarza@jgarza-laptop:~$ dpkg --get-selections | grep ka
kernel-package                                  deinstall
libkadm55                                       deinstall
python-kaa-base                                 deinstall
python-kaa-imlib2                               deinstall
python-kaa-metadata                             deinstall
ttf-kannada-fonts                               deinstall


From the man page I think this means it is set to be removed, how do I get it where it doesn't show up anywhere?

---

### Post by karth on 2007-10-23
try ```
sudo aptitude purge pkgname
```
This will deselect the package and physically remove the files from the hdd

---

### Post by johndela1 on 2007-10-23
can this be done with the apt programs?

I'm trying to understand the apt tools.  I'm a little confused now.

I just did a sudo apt-get install python-kaa-base then I did a
sudo apt-get remove python-kaa-base.  Then when I checked  with
dpkg --get-selections | grep python-kaa-base, it was gone.  Earlier when I
checked with dpkg --get-selections | grep python-kaa-base, I saw it was listed
but said deinstall.


Does this have anything to do with the fact that remove leaves stuff behind
but purge completly removes it?

this is another thing that I don't get

I do this:
jgarza@jgarza-laptop:~$ dpkg --get-selections | grep xterm
xterm                                           deinstall


I never removed xterm and when I try to install it it is says it is already
there.




I guess I don't understand the apt tools.  Is there a tutorial that covers
my questions?  Maybe I'm not reading right, but the man page seems like
it doesn't explain how these things work.

---

### Post by johndela1 on 2007-10-29
Let me ask a simpler question...

Why do I see this: 

jgarza@jgarza-laptop:~/qemu$ dpkg --get-selections | grep postf
postfix                                         deinstall
jgarza@jgarza-laptop:~/qemu$ 



I never removed postfix.  As a matter of fact, I recently installed it.



another question:

If I do a apt-get remove foo, I still see foo but it says deinstall.  Once I'm at this point, how do I purge it?  It seems like I need to reinstall it then purge it.

---


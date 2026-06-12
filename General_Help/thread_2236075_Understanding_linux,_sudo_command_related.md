---
title: "Understanding linux, sudo command related"
date: 2014-07-24
forum: General Help
---

### Post by linux_dream on 2014-07-24
Hello,
I have found a command in [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto), which is ```
dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge
```.
The website states that > While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command..
So I tried the command, it returned > dpkg: error: requested operation requires superuser privilege.  So I tried to use sudo..., but it returned: ```
dpkg: error: requested operation requires superuser privilege
```.
I sought help in a chess forum and the guy told me to open xterm with sudo and then type the command. This returned: ```
dpkg: error: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked
[*] produce a lot of output - pipe it through 'less' or 'more' !

```. 
He then told me to try the normal LXterminal and to add "sudo" just before "xargs". This returned ```
dpkg: error: --purge needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked
[*] produce a lot of output - pipe it through 'less' or 'more' !

```.
Finally I found the "fix" myself:  "sudo su" and then type the command, that removed a few packages.

I am trying to understand why "sudo" failed in the first place, why "sudo su" was required and why placing "sudo" in front of "xargs" gave exactly the same result as being root in Xterm and still failed to execute the command as it should. I would appreciate some help and explanations on what's going on. 
Thank you very much.

---

### Post by Impavidus on 2014-07-24
dpkg -l lists all packages with status other than un (+ a header). These are piped in:
grep, which filters it to get only the lines starting with rc, that is, the uninstalled packages with remaining config files, which is then piped into
awk, picking the second word, wich is the package name, which is piped into
xargs, which adds them to the command line of dpkg --purge.

The first try didn't succeed becaus you were not root. Adding sudo to the front of the command ran only dpkg -l with root privileges, which didn't help. Running it from a root shell or inserting sudo to get xargs sudo dpkg --purge runs dpkg --purge <arguments> with root privileges, which is what you needed. They should both give the same result. I think this should have worked, except when there were no packages with remaining configuration files, which would lead to the error messages you recieved ("needs at least one package name"). If you are positive there were packages to be purged, then I don't know.

---

### Post by linux_dream on 2014-07-24
Ok I see, thank you very much. 
Indeed now "sudo su" + the command, returns exactly the same message than sudo in front of xargs. 
Problem solved, I suppose.

---

### Post by Lars Noodén on 2014-07-24
Also, if you are using awk then it is rare to need grep, too.  Awk has most of the same capabilities.

```

dpkg -l | awk '/^rc/ {print $2}'
dpkg -l | awk '$1 == "rc" {print $2}'

```

---


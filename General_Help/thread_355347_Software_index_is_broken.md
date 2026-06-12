---
title: "Software index is broken"
date: 2007-02-07
forum: General Help
---

### Post by Stone_Wolf on 2007-02-07
I had a notification of updates for my machine, but when i went to install them...i get this error.

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

But when i go to run "sudo apt-get install -f" in the terminal, i get this error.

invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm still rather new to the whole samba thing, i'm only just beginning to learn the basic of it now. But i have no idea what this error means. Is it fixable, or should i consider a reload?

Any help provided will be greatly appreciated.

Regards
SW

---

### Post by raul_ on 2007-02-07
Try

```
sudo dpkg -configure -a 
```

---

### Post by Stone_Wolf on 2007-02-07
Hiyas

Thanks for the speedy response. Unfortunately it hasn't solved anything. When i try that command, all i get is this.

dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

I fiddled about a little on my own, and somewhere along the lines i came across this gem

invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba

Could this be related to my samba problems?

---

### Post by Stone_Wolf on 2007-02-07
Problem solved!  

After stumbling about for a while i came across this post

[http://www.ubuntuforums.org/showthread.php?t=214848](http://www.ubuntuforums.org/showthread.php?t=214848)

Seems i'm not the only one having hassles with the update for samba.

Well, it's all working now. Thanks for the help  ;)

Regards
SW

---


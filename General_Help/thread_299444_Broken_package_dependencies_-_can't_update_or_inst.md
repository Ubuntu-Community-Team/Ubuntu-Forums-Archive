---
title: "Broken package dependencies - can't update or install anything"
date: 2006-11-14
forum: General Help
---

### Post by jude999 on 2006-11-14
Since I upgraded to Edgy, I always had 1 update that wouldn't go through: uim-common that seems to be a package that has smth to do my being able to write Chinese characters on my computer. I am not the one who installed it so I am not quite sure.

I tried a couple things to resolve that problem an failed. Now I can't install anything new or run update manager.

What should I do to get everything up and running again?

Thanks

here is what happens when I run apt-get install -f:

```
simon@simon:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  uim-common
The following packages will be upgraded:
  uim-common
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/819kB of archives.
After unpacking 336kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 112049 files and directories currently installed.)
Preparing to replace uim-common 1:1.0.0-1ubuntu1 (using .../uim-common_1%3a1.2.1-3ubuntu2_all.deb) ...
ERROR: unbound variable (errobj is-set-ugid?)

*backtrace*
>>(is-set-ugid?)
>>(if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ()))))
>>(define uim-plugin-lib-load-path (if (is-set-ugid?) (list (string-append (sys-pkglibdir) "/plugin")) (filter string? (append (list (getenv "LIBUIM_PLUGIN_LIB_DIR") (string-append (getenv "HOME") "/.uim.d/plugin") (string-append (sys-pkglibdir) "/plugin")) (if (getenv "LD_LIBRARY_PATH") (string-split (getenv "LD_LIBRARY_PATH") ":") ())))))
>>(require "plugin.scm")
>>(require "init.scm")
>>(*catch (quote errobj) (require "init.scm"))
>>(eq? (quote *init.scm-loaded*) (*catch (quote errobj) (require "init.scm")))

ERROR: unbound variable (errobj custom-reload-customs)

ERROR: unbound variable (errobj custom-choice-rec-sym)

ERROR: unbound variable (errobj plugin-alist)

ERROR: wta to car (errobj t)

dpkg: error processing /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2_all.deb (--unpack):
 dpkg: warning - old pre-removal script killed by signal (Interrupt)

Errors were encountered while processing:
 /var/cache/apt/archives/uim-common_1%3a1.2.1-3ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jude999 on 2006-11-14
Somebody, please... I don't want to have to go through a clean install of my system...

---

### Post by satshen on 2006-11-14
Hi

Have you tried

 dpkg  -- configure -a 

I had a similar problem sometime back - couldn't do any further updates. The above command  resolved the issue, but I am not sure how 

Cheers 

Satshen

---

### Post by jude999 on 2006-11-14
> **satshen said:**
> Hi

Have you tried

 dpkg  -- configure -a 

I had a similar problem sometime back - couldn't do any further updates. The above command  resolved the issue, but I am not sure how 

Cheers 

Satshen

Thanks for the suggestion, I tried and got a whole buch of errors:

```
simon@simon:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
simon@simon:~$ sudo dpkg --configure -a
Password:
dpkg: dependency problems prevent configuration of uim-fep:
 uim-fep depends on uim-common (>= 1:1.2.1-3ubuntu2); however:
  Version of uim-common on system is 1:1.0.0-1ubuntu1.
dpkg: error processing uim-fep (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of uim:
 uim depends on uim-fep; however:
  Package uim-fep is not configured yet.
dpkg: error processing uim (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of uim-gtk2.0:
 uim-gtk2.0 depends on uim-common (>= 1:1.2.1-3ubuntu2); however:
  Version of uim-common on system is 1:1.0.0-1ubuntu1.
dpkg: error processing uim-gtk2.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of uim-xim:
 uim-xim depends on uim-common (>= 1:1.2.1-3ubuntu2); however:
  Version of uim-common on system is 1:1.0.0-1ubuntu1.
dpkg: error processing uim-xim (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 uim-fep
 uim
 uim-gtk2.0
 uim-xim

```

Any other idea?

---

### Post by jude999 on 2006-11-14
Please?

---

### Post by CyclopsU on 2006-11-14
The geeks will laugh at me but this is how I corrected the same problem. I went to my Synaptic Package Manager and manually scrolled through the packages. This can take a while. Your installed packages have a green marker and any broken packages will have a red marker. When I uninstalled my broken package everything worked once again. Updates have worked flawlessly ever since.

---

### Post by jude999 on 2006-11-14
it'a actually when I tried to uninstall that package that I messed things up... so synaptic is no help for me, I can not update the packages because I am missing a library that is not available in my repositaries (libuim0)

I am trying a solution right now: Going back to the drapper universe repos as apparently the lib is in there and might be available... Lots of fun :S

---

### Post by jude999 on 2006-11-14
Well, thanks for those who tried to help help here.

I managed to get my update manager to work again, no more broken pakages.

I will not go into detailed explanations on how I did it as it is 4 hours of trying.
It involved going back to the drapper repos, downloading the libuim0 deb, forcing its installation (forcing overwriting as didn't originally allowed me to)...

I learned a lot of command lines tonight, and a lot about my sistem.

I still can't upgrade uim-common, I don't know why, but I'll look into it tomorrow. if anybody has an idea or suggestion, here is what my computer tells me when I try:

```
go to bed!
```

---

### Post by drkeuk on 2006-12-17
This thread has a solution. It worked fine for me!

[http://www.ubuntuforums.org/showthread.php?t=286944](http://www.ubuntuforums.org/showthread.php?t=286944)

---


---
title: "pspp emacs conflict"
date: 2015-02-17
forum: General Help
---

### Post by monkeybrain20122 on 2015-02-17
Hi, 

I am trying to install emacs on Ubuntu 14.04 and get these errors
```

Setting up libotf0:amd64 (0.9.13-1ubuntu1) ...
Setting up emacsen-common (2.0.7) ...
Setting up emacs24-common-non-dfsg (24.3+1-1) ...
Setting up emacs24-common (24.3+1-2ubuntu1) ...
Setting up emacs24-bin-common (24.3+1-2ubuntu1) ...
update-alternatives: using /usr/bin/ctags.emacs24 to provide /usr/bin/ctags (ctags) in auto mode
update-alternatives: using /usr/bin/ebrowse.emacs24 to provide /usr/bin/ebrowse (ebrowse) in auto mode
update-alternatives: using /usr/bin/emacsclient.emacs24 to provide /usr/bin/emacsclient (emacsclient) in auto mode
update-alternatives: using /usr/bin/etags.emacs24 to provide /usr/bin/etags (etags) in auto mode
update-alternatives: using /usr/bin/grep-changelog.emacs24 to provide /usr/bin/grep-changelog (grep-changelog) in auto mode
Setting up m17n-db (1.6.4-1) ...
Setting up m17n-contrib (1.1.14-1) ...
Setting up libm17n-0 (1.6.4-2ubuntu1) ...
Setting up emacs24 (24.3+1-2ubuntu1) ...
update-alternatives: using /usr/bin/emacs24-x to provide /usr/bin/emacs (emacs) in auto mode
Install emacsen-common for emacs24
emacsen-common: Handling install of emacsen flavor emacs24
Wrote /etc/emacs24/site-start.d/00debian-vars.elc
Wrote /usr/share/emacs24/site-lisp/debian-startup.elc
Install pspp for emacs24
install/pspp: Handling install for emacsen flavor emacs24
/usr/lib/emacsen-common/packages/install/pspp: 34: cd: can't cd to /usr/share/emacs/site-lisp/pspp
ERROR: install script from pspp package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs24 | emacs24-lucid | emacs24-nox; however:
  Package emacs24 is not configured yet.
  Package emacs24-lucid is not installed.
  Package emacs24-nox is not installed.

dpkg: error processing package emacs (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 emacs24
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


It seems that emacs has a pspp module which is in conflict with pspp already installed (if remove pspp then emacs installs fine, but reinstalling pspp gives errors )

Any suggestion?

---

### Post by Holger_Gehrke on 2015-02-20
> **monkeybrain20122 said:**
> 
... snip ...
```

install/pspp: Handling install for emacsen flavor emacs24
/usr/lib/emacsen-common/packages/install/pspp: 34: cd: can't cd to [COLOR=#ff0000]/usr/share/emacs/site-lisp/pspp[/COLOR]
ERROR: install script from pspp package failed

```
...snip...
It seems that emacs has a pspp module which is in conflict with pspp already installed (if remove pspp then emacs installs fine, but reinstalling pspp gives errors )

Any suggestion?

Have you checked whether the directory it tries to 'cd' to exists and if it does what the permission for it are ? I've taken a look in some of the scripts in '/usr/lib/emacsen-common/packages/install' and they usually create the directory for their package files, copy or move them there and byte-compile them. 

It seems to me more like PSPP left an install script lying in wait to install an emacs mode if emacs gets installed. This script should probably get called towards the end of the emacs install but gets called to early or has a bug ... you could try moving the script '/usr/lib/emacsen-common/packages/install/pspp' away, installing emacs, put the script back and call it manually.

---

### Post by monkeybrain20122 on 2015-02-21
Hi, 

You are right. The directory /usr/share/emacs/site-lisp/pspp does not exist. I created the folder manually and installed emacs again this time I get the error
```
Install pspp for emacs24
install/pspp: Handling install for emacsen flavor emacs24
cp: cannot stat ‘pspp-mode.el’: No such file or directory
ERROR: install script from pspp package failed
dpkg: error processing package emacs24 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs24 | emacs24-lucid | emacs24-nox; however:
  Package emacs24 is not configured yet.
  Package emacs24-lucid is not installed.
  Package emacs24-nox is not installed.

dpkg: error processing package emacs (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          E: Sub-process /usr/bin/dpkg returned an error code (1)


```


It maybe a bug in the script /usr/lib/emacsen-common/packages/install/pspp moving it and emacs installs successfully.

Thanks for the help.

---

### Post by monkeybrain20122 on 2015-02-22
Does anyone know which package  pspp-mode.el is supposed to come from? Thanks

---

### Post by monkeybrain20122 on 2015-05-19
Same problem in Ubuntu 15.04.

---

### Post by SeijiSensei on 2015-05-20
One workaround is to install [**jed**]("http://www.jedsoft.org/jed") instead of emacs.  Jed defaults to the emacs interface.  I've used it for years having once learned emacs keystrokes.

---

### Post by monkeybrain20122 on 2015-05-20
> **SeijiSensei said:**
> One workaround is to install [**jed**]("http://www.jedsoft.org/jed") instead of emacs.  Jed defaults to the emacs interface.  I've used it for years having once learned emacs keystrokes.

Thanks for the suggestion but it won't work because I need emacs .deb packages from repo as dependencies  for something else.

My solution now is to simply remove pspp and then install it from source locally in my $HOME. This is easy enough except on Unity it crashes whenever opening a data file. I fixed this with a patch from [https://launchpad.net/~adamzammit/+archive/ubuntu/pspp/+sourcepub/4490703/+listing-archive-extra](https://launchpad.net/~adamzammit/+archive/ubuntu/pspp/+sourcepub/4490703/+listing-archive-extra)

So my problem is solved but I will leave this thread open in case someone comes up with a proper solution.

---

### Post by monkeybrain20122 on 2015-05-20
Ok, I think it is a packaging bug in pspp so there isn't much can be done here. I think my solution (compiling pspp locally) is as good and proper as it can be. I have contacted the maintainer of the pspp package and I will just mark this as solved.

---

### Post by monkeybrain20122 on 2015-06-15
Update: the maintainer of the pspp ppa has fixed the problem.

---


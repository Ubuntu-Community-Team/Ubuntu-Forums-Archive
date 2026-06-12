---
title: "Cannot install Gnucash"
date: 2014-12-03
forum: General Help
---

### Post by leunam12 on 2014-12-03
I have been running gnucash for years, now it stopped working and was removed by an upgrade. When I try to re-install it I get an error

```
The following packages have unmet dependencies:

gnucash: Depends: gnucash-common (= 1:2.6.4-1~getdeb2~utopic) but 1:2.6.4-1~getdeb2~utopic is to be installed
         Depends: libofx6 but it is not going to be installed


```

Any help will be appreciated.

Thanks

---

### Post by amanchesterman on 2014-12-03
Are you trying to install it from the Software Center? Or you could use Synaptic. Both of those manage the dependencies OK in my experience.

---

### Post by leunam12 on 2014-12-03
I get the same error from both.

---

### Post by ian-weisser on 2014-12-03
> **leunam12 said:**
> gnucash: Depends: gnucash-common (= 1:**2.6.4-1~getdeb2~utopic**) but 1:2.6.4-1~getdeb2~utopic is to be installed
         Depends: libofx6 but it is not going to be installed

Seems like are trying to install GnuCash from a PPA or other non-Ubuntu source instead of the Ubuntu repositories.
Usually,that means there is a version conflict or a file conflict.

If you are curious about the specific problem, try installing any of those blocked packages. The error messages will provide the specific issue, but usually won't tell you what caused it (non-Ubuntu software) or how to fix it (uninstall the offending software).

If you just want to fix it, then:
1) Uninstall all the software provided by that non-Ubuntu source.
2) Disable that source, so it won't pull the lousy in again.
3) Reinstall any desired applications from the Ubuntu repositories.

If you need help with any of those steps, please just say so. It's not difficult, but might be a bit confusing if it's your first time exploring the package manager.

---

### Post by rbmorse on 2014-12-03
GnuCash 2.6.4 is a new release that hasn't made it into repository, yet (latest for Utopic is 2.6.3).  

GnuCash 2.6.4 and related packages are available in repository for the next Ubuntu (vivid) as well as the Ubuntu Packages web page ([http://packages.ubuntu.com/vivid/](http://packages.ubuntu.com/vivid/)). I do not recommend trying to install these since there may be dependencies for GnuCash 2.6.4 that break things in earlier versions of Ubuntu.  

You can spend an entire afternoon chasing down and installing upgraded packages only to find your basic installation no longer operates properly, so a reliable backup of your existing Ubuntu is mandatory before pursuing this route (don't ask me how I know this). 

It is also possible that someone with genuine skills in package development will backport the new version of GnuCash (and dependencies) to the Utopic repository. I have no idea about how to request this, but there may be a procedure in the community user's guide

---

### Post by leunam12 on 2014-12-03
I am not trying to install any particular version, just Gnucash from the Software Center. I always install it from the software center and it was working fine until yesterday, but today it was uninstalled by an upgrade. I didn't uninstall it, the upgrade did. When I try to install it again I get this error. so I guess there is some repository that I have to disable because it's pulling a beta version or something like that instead of the ubuntu 14.04 version, am I right?

So how I disable this repository?

---

### Post by rbmorse on 2014-12-03
It would be helpful to know which upgrade caused the problem...maybe check the  /var/log/apt directory.  Also, is the file libofx6 currently installed (use synaptic, if you have that) and if so, what version?

---

### Post by ian-weisser on 2014-12-03
> **leunam12 said:**
> I am not trying to install any particular version, just Gnucash from the Software Center. I always install it from the software center and it was working fine until yesterday, but today it was uninstalled by an upgrade. I didn't uninstall it, the upgrade did. When I try to install it again I get this error. so I guess there is some repository that I have to disable because it's pulling a beta version or something like that instead of the ubuntu 14.04 version, am I right?

So how I disable this repository?

Let's be a bit more clear.
You added a source and installed software that caused the version conflict. The problem you have seems to be a simple version conflict.
The dpkg error message gave us the facts that led to the conclusion. Nothing mysterious about it. No need to guess.

1) To disable the repository, look in System Setting --> Software & Updates --> Other Software
Uncheck the appropriate box. If you don't know which box to uncheck, look for 'getdeb'.

2) You must also delete the removed package from your system's cache. To be thorough, let's delete all the cached packages.
```
sudo apt-get clean
```

3) You should also ensure all PPA-provided dependencies are removed.
```
sudo apt-get autoremove gnucash
```

4) Finally, after the 'getdeb' repository is disabled, let's refresh the system's database of packages, then let's install GnuCash from the Ubuntu Repositories (the only remaining choice):
```
sudo apt-get update
sudo apt-get install gnucash
```

---

### Post by leunam12 on 2014-12-03
Sounds like a plan!!! I'll do that as soon as I get home. :D

---

### Post by leunam12 on 2014-12-03
Done! Marked as solved. Thank you very much. Now I remember adding getdeb to install a new version of Avidemux because the one in the Ubuntu repositories has a bug. Thanks again

---


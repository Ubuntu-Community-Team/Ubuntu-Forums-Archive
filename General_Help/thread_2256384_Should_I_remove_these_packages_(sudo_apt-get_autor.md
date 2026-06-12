---
title: "Should I remove these packages (sudo apt-get autoremove)?"
date: 2014-12-11
forum: General Help
---

### Post by Darth Riker on 2014-12-11
Hi there,

Just a question in regards to using sudo apt-get autoremove. I was just wanting to basically make sure all was running clean (just some housekeeping) and was confused by the output of this command:

```

The following packages will be REMOVED:
  hyphen-en-us libreoffice-help-en-gb libreoffice-help-en-us
  libreoffice-l10n-en-gb libreoffice-l10n-en-za linux-headers-3.13.0-32
  linux-headers-3.13.0-32-generic linux-image-3.13.0-32-generic
  linux-image-extra-3.13.0-32-generic mythes-en-au mythes-en-us
  openoffice.org-hyphenation
0 to upgrade, 0 to newly install, 12 to remove and 23 not to upgrade.
After this operation, 322 MB disk space will be freed.

```

Is it ok for me to go ahead and remove those packages?

I do use LibreOffice Version: 4.2.7.2 Build ID: 420m0(Build:2) - so wasn't sure why those LibreOffice packages were being marked for removal ...

---

### Post by bobthebaritone on 2014-12-12
Hi Darth Riker,

The packages listed in your output above are only part of the suite of packages that may/may not be installed for Libre Office.

What I would suggest you do to ensure you have the correct version is to actually start Libre Office, and get the version from help/about. Start Libre Office from the "libre Office" Icon. If you start Libre Office from the particular office application you will not get the opportunity to get the Help/About option. See attached.

You can compare this to currently installed libre office from the command line using -
[SIZE=1][FONT=lucida console]dpkg -l | grep libre | more[/FONT][/SIZE].
It is pretty straight forward to see what version you have. You can then be confident to do the auto remove.

I expect that it is time to do a dist-upgrade as you have packages held back.

I note also that the openoffice hyphenation package is on my newly installed Ubuntu 14.10.

Hope this helps,

Bob

---

### Post by sudodus on 2014-12-12
In general it is safe to allow ```
sudo apt-get autoremove
``` do its job. From ```
man apt-get
```

```
       autoremove
           autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for other packages and are now no longer needed.

```

---

### Post by sudodus on 2014-12-12
> **bobthebaritone said:**
> ...

I expect that it is time to do a dist-upgrade as you have packages held back.


+1 :-)

```

sudo apt-get update
sudo apt-get dist-upgrade

```

```
man apt-get
```

tells us

```
       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles
           changing dependencies with new versions of packages; apt-get has a "smart" conflict
           resolution system, and it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade command may remove some
           packages. The /etc/apt/sources.list file contains a list of locations from which to
           retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding
           the general settings for individual packages.

```

---

### Post by Darth Riker on 2014-12-12
Thanks guys. All has worked great.

Just a follow up question (before I mark this as solved).

In regards to the command:

```
sudo apt-get dist-upgrade
```

How come these aren't done when running the Software Updater program from the Applications Menu?

---

### Post by ajgreeny on 2014-12-12
Packages such as new kernels that could cause problems due to proprietary drivers are not installed by default when running apt-get upgrade or the software-updater, partly because they are not just upgrades but are actually new packages.

If you only use open source drivers it is generally safe to update everything with the dist-upgrade command or by using synaptic, which is how I have been updating for the last 9 years, since version 5.04 without any problems.

---

### Post by Darth Riker on 2014-12-12
Ah. Understood. Thank you.

---


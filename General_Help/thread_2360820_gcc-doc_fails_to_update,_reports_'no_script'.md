---
title: "gcc-doc fails to update, reports 'no script'"
date: 2017-05-08
forum: General Help
---

### Post by Xiguus on 2017-05-08
Hi All,

Since upgrading my 64-bit installation from 14.04 to 16.04 I have had an ongoing problem with packages gcc-doc and cpp-doc.
Installed versions are 4.8.2; current versions, as reported by synaptic, is 5.3.1.
Software updater notifies me of the updated software but the action fails with the message:
```
E: /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb: there is no script in the new version of the package - giving up
E: /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb: there is no script in the new version of the package - giving up

```
Synaptic also identifies the updates but fails with the following:
```

N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
(Reading database ... 657152 files and directories currently installed.)
Preparing to unpack .../cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Preparing to unpack .../gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb ...
install-info: No dir file specified; try --help for more information.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-doc_4%3a5.3.1-1ubuntu1_amd64.deb
 /var/cache/apt/archives/gcc-doc_4%3a5.3.1-1ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing package gcc-doc (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: error processing package cpp-doc (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 gcc-doc
 cpp-doc

```
These two packages have also caused problems with other update tasks, including kernel updates, causing them to fail. I have tried unmarking the packages in synaptic, but they will not unmark and will not delete.
I have also tried to delete the packages with dpkg, eg
```
sudo dpkg --force-remove-reinstreq -r gcc-doc cpp-doc
```
without success.

Is there a fix?

Best Regards,

Xiguus

---

### Post by Xiguus on 2017-05-09
Hi again,

I've had a look around and found some bug reports:[URL="https://bugs.launchpad.net/bugs/1609854"]
[/URL][https://bugs.launchpad.net/bugs/1577192](https://bugs.launchpad.net/bugs/1577192) 
[https://bugs.launchpad.net/bugs/1609854](https://bugs.launchpad.net/bugs/1609854)
[URL="https://bugs.launchpad.net/bugs/1614208"]https://bugs.launchpad.net/bugs/1614208
[/URL][https://bugs.launchpad.net/bugs/1615896](https://bugs.launchpad.net/bugs/1615896)

Looks like this problem has been around for a while...

BR,

Xig

---

### Post by Xiguus on 2017-05-18
Hi All,

OK so nothing has been done (yet) about fixing 5.3.1, I'm sure it will happen sometime, not to worry...
My objective now is to uninstall 4.8.2, which is obstructing my package upgrades and preventing me from deleting old kernels etc.

Answer to this is at
[https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error](https://askubuntu.com/questions/148715/how-to-fix-package-is-in-a-very-bad-inconsistent-state-error)

```

$ sudo mkdir /tmp/gccdox   ##give it somewhere to live
$ sudo mv /var/lib/dpkg/info/gcc* /tmp/gccdox   ##no gcc-doc files for dpkg to work on
$ sudo dpkg --remove --force-remove-reinstreq gcc-doc
```

which gives us:

```

dpkg: warning: overriding problem because --force enabled:
dpkg: warning: package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
dpkg: warning: files list file for package 'gcc-doc' missing; assuming package has no files currently installed
(Reading database ... 657147 files and directories currently installed.)
Removing gcc-doc (4:4.8.2-1ubuntu6) ...

```

I have seen it said that using the "--force-remove-reinstreq" option can destroy your system because it will purge all dependencies of a package including those needed by other packages. This isn't an issue with gcc-doc, so the command is safe.

Do the same for cpp-doc.

Tell apt what has happened:
```

$ sudo apt-get remove gcc-doc
```

and get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gcc-doc' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  ...
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

Repeat for cpp-doc.

Clean up:
```

$ sudo apt-get autoremove
$ sudo apt-get autoclean
```

All of this worked wthout fuss or incident, gcc-doc and cpp-doc are no longer showing as installed in synaptic or in any oher package management tools and are no longer aborting my upgrades. For these reasons I have marked the problem as "solved", even though the xenial packages still do not install. I am regarding this as a separate matter, in the hands of the package managers.

Best Regards,

Xiguus

---


---
title: "I can't install emacs in ubuntu 22.04"
date: 2022-05-10
forum: General Help
---

### Post by econdami on 2022-05-10
Hello,
I generally use Fedora so I don't know all the subtleties of Ubuntu (although we are closer than for windows and Mac!!!).
I use a Singularity container in which there is Ubuntu installed. The last version of the container had ubuntu-18.04. In this image
I managed to install emacs very easily by doing:
```
apt-get install -y software-properties-common
add-apt-repository ppa:kelleyk/emacs
apt update
apt install emacs26
```
The new version I just installed has ubuntu-22.04. When I do the same commands to install emacs it does not work:
```
Singularity> add-apt-repository ppa:kelleyk/emacs
PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu/ jammy main'
Description:
This repository contains updated `emacs` packages based on stable releases.

The following package series are available:
  - `emacs27`: based on 27.x-series releases.
  - `emacs26`: based on 26.x-series releases.
  - `emacs25`: based on 25.x-series releases.

The `emacs27` packages have `cairo`-based text rendering; this may cause issues with bitmapped fonts.  They add native JSON manipulation, ACL support, and version-dependent 'load-path entries (like what the Ubuntu packages have), and more.  The `emacs27` packages for 16.04 LTS (xenial) no longer include xwidgets support due to an upstream change that requires newer libraries.

On top of each series, I have applied the following patches:
  - A fix for an `xinput`-related bug that, when triggered, causes `emacs` to enter an infinite loop; the process will then be unresponsive and will consume 100% of a single CPU core until you kill it.

An ELPA signing key expired in 2019-09.  The new key, which is valid until 2024, is included Emacs 26.3 and later.  I have also backported it to the `emacs25` series.  If you have an existing install that is affected by the key expiration, instructions on fetching the new key and inserting it into the keychain are available here: https://elpa.gnu.org/packages/gnu-elpa-keyring-update.html

Debug symbols are available!  After adding the PPA however you normally do, find the corresponding entry in `/etc/apt/sources.list.d`.
It will look like the first line below (though the suite name may be different if you are not using focal); duplicate it and change the component name ("main") to "main/debug".
  deb http://ppa.launchpad.net/kelleyk/emacs/ubuntu focal main
  deb http://ppa.launchpad.net/kelleyk/emacs/ubuntu focal main/debug

The packaging was originally based on that from the `emacs-snapshot` PPA.
The source packages that I upload are built from a packaging repository (https://github.com/kelleyk/ppa-emacs) with the help of my `kk-debuilder` utility (described at https://github.com/kelleyk/kk-debuilder).
  $ kk-debuilder --target=xenial,bionic,focal,hirsute,impish --no-check --debian-branch=master-emacs27.2 --upstream-branch=upstream-emacs27.2 --source-only

If you want to build binary packages yourself, note that you may run into trouble unless you disable ASLR.
  $ echo 0 | sudo tee /proc/sys/kernel/randomize_va_space
Remember to re-enable it once the build is complete.
  $ echo 2 | sudo tee /proc/sys/kernel/randomize_va_space

Change history highlights:
  - 27.1~1.git86d8d76aa3-kk1: The 'load-path has been changed to include
    version-specific directories like the Ubuntu/Debian packages do.  The
    packages now also provide the non-version-specific package names used
    by the Ubuntu packages (e.g. emacs27-common provides emacs-common).
  - 25.3~2.gitc09215a-kk1: I have backported the 2019 ELPA signing key,
    which is valid until 2024.
  - 25.1~1.gitf0eb70d-kk8: I have experimentally enabled debug symbols
    (`-dbgsym` packages) and non-x86 architectures in this PPA's settings.
  - 25.1~1.gitf0eb70d-kk4: The GTK and -nox packages have had
    --with-modules and --with-file-notification added to their build-time
    configuration.
More info: https://launchpad.net/~kelleyk/+archive/ubuntu/emacs
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Found existing deb entry in /etc/apt/sources.list.d/kelleyk-ubuntu-emacs-jammy.list
Adding deb entry to /etc/apt/sources.list.d/kelleyk-ubuntu-emacs-jammy.list
Found existing deb-src entry in /etc/apt/sources.list.d/kelleyk-ubuntu-emacs-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/kelleyk-ubuntu-emacs-jammy.list
Adding key to /etc/apt/trusted.gpg.d/kelleyk-ubuntu-emacs.gpg with fingerprint 873503A090750CDAEB0754D93FF0E01EEAAFC9CD
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease                                 
Hit:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                                   
Hit:4 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                                 
Ign:7 https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy InRelease                                                                                                                              
Get:5 https://neurodebian.g-node.org data InRelease [30.2 kB]                                                                                                    
Err:8 https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy Release                                                                                        
  404  Not Found [IP: 2001:67c:1560:8008::19 443]
Get:6 https://neurodebian.g-node.org focal InRelease [18.2 kB]                                                                   
Hit:9 https://packagecloud.io/github/git-lfs/ubuntu bionic InRelease                                                  
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://neurodebian.g-node.org/dists/data/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: http://neurodebian.g-node.org/dists/focal/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://packagecloud.io/github/git-lfs/ubuntu/dists/bionic/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Singularity> apt update
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                                                                                                 
Hit:3 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                                                               
Ign:4 https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy InRelease                                                                                                                                    
Hit:6 http://security.ubuntu.com/ubuntu jammy-security InRelease                                                                                                  
Err:8 https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy Release                                                                                                                                 
  404  Not Found [IP: 2001:67c:1560:8008::19 443]
Get:5 https://neurodebian.g-node.org data InRelease [30.2 kB]                                                                                                                                            
Get:7 https://neurodebian.g-node.org focal InRelease [18.2 kB]                                             
Hit:9 https://packagecloud.io/github/git-lfs/ubuntu bionic InRelease
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/kelleyk/emacs/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://neurodebian.g-node.org/dists/data/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: http://neurodebian.g-node.org/dists/focal/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: https://packagecloud.io/github/git-lfs/ubuntu/dists/bionic/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Singularity> apt install emacs26
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package emacs26 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'emacs26' has no installation candidate

```

it looks like the package is not available. What can I do in this case?

---

### Post by Holger_Gehrke on 2022-05-10
The PPA you're trying to use doesn't offer packages for 22.04 (yet ?). If you can live with having an emacs of the 27.x series, than the standard repositories offer the packages emacs-gtk (graphical, GTK-based UI) or emacs-nox (text-mode / terminal only).

Holger

---

### Post by econdami on 2022-05-10
Oh yes! Thanks a lot, ```
apt install emacs-gtk 
```did exactly what I wanted!

---


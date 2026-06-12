---
title: "How to fix the Firestarter GUI crash bug [Gutsy]"
date: 2008-01-31
forum: General Help
---

### Post by frogotronic on 2008-01-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello,

  Here is how to fix a irritating problem with the Firestarter firewall GUI crashing.  This is taken from "robneild" & "MLIND" who first posted it to the following bug report on launchpad: [120445]("https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/120445")

    (*Note: the GUI crash doesn't affect the firestarter firewall - it is still running in the background, so if you're uncomfortable with this howto, its entirely optional*)

```
sudo apt-get build-dep firestarter
```

This will likely install A LOT of libraries - its okay, you need them to continue.

```
sudo apt-get install fakeroot
apt-get source firestarter
cd firestarter-1.0.3/src/
```

At this point we need to change the version (#) of the *.deb file we're going to create, otherwise the Update Manager is going to continually ask/remind you that there is an update (which, in fact won't be true, it will try to "update" to the unpatched (broken) version of firestarter and you'll be right back where you started before applying the patch).

```
sudo apt-get install devscripts
dch -i firestarter_1.0.1-6ubuntu1_i386.deb
```

Get the patch (or download it from this post)

```
wget http://launchpadlibrarian.net/11480727/foo2.patch
patch < foo2.patch
cd ..
```

Now, build the new firestarter deb package..

```
dpkg-buildpackage -rfakeroot
cd ..
```

Now, install

```
sudo dpkg -i firestarter_1.0.3-6ubuntu2_i386.deb
```

You should have a patched & installed firestarter whose GUI no longer crashes.

Good Luck!

- CH

---

### Post by cor2y on 2008-02-16
Thanks for the howto on patching this.
It worked for me i was really getting tired of firestarter crashing anytime you tried any of the tabs or drop down menus.

---

### Post by frogotronic on 2008-02-16
Welcome.

I think this "patch" is going to be pushed into the repos as a 1.1 increment as opposed to a 2 increment on the deb.  Unfortunately, I don't know how to change the increment to increase by only 0.1 as opposed to 1.0.

- CH

---

### Post by cisforcojo on 2008-02-24
Genius, sir. Pure genius.

---

### Post by ixlam on 2008-06-17
Hello. 
Ive previously patched my Firestarter GUI with success.
(Gusty 7.1 RT kernel with all updates on 32 bit machine)

This time I tried to change the default ICONS to Green (notification) and replaced the "Launcher" icon with one of same size etc.

after I run > dpkg-buildpackage -rfakeroot

I get the following error
```

dpkg-buildpackage: source package is firestarter
dpkg-buildpackage: source version is 1.0.3-6ubuntu2
dpkg-buildpackage: source changed by marrs <marrs@ubu>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.0.3-6ubuntu2
 fakeroot debian/rules clean
dpatch  deapply-all  
17_update_docs_uri not applied to ./ .
15_update_sv_po not applied to ./ .
14_update_non_routables not applied to ./ .
13_browser_nonroot not applied to ./ .
12_firestarter_transparent_icon not applied to ./ .
11_desktop_file not applied to ./ .
10_dhcp_hook not applied to ./ .
09_fix_ip_up not applied to ./ .
06_dot_not_hyphen not applied to ./ .
05_remove_INSTALL_from_README not applied to ./ .
03_xpm_icon not applied to ./ .
02_restart_dnsmasq not applied to ./ .
02_restart_dhcp3-server not applied to ./ .
02_detect_dhcp3-server_correctly not applied to ./ .
01_use_gksu not applied to ./ .
rm -rf patch-stamp patch-stampT debian/patched
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
rm -f intltool-extract intltool-update intltool-merge
rm -f firestarter.schemas firestarter.desktop
[ ! -f Makefile ] || /usr/bin/make distclean
rm -f config.log config.status
dh_clean
rm -f po/*.gmo
 dpkg-source -b firestarter-1.0.3
dpkg-source: building firestarter using existing firestarter_1.0.3.orig.tar.gz
dpkg-source: building firestarter in firestarter_1.0.3-6ubuntu2.diff.gz
dpkg-source: cannot represent change to pixmaps/firestarter.png: binary file contents changed
dpkg-source: cannot represent change to src/xpm/icon_start_large.png: binary file contents changed
dpkg-source: cannot represent change to src/xpm/icon_start_normal.png: binary file contents changed
dpkg-source: warning: executable mode 0755 of 'debian/patches/03_xpm_icon.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/17_update_docs_uri.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/05_remove_INSTALL_from_README.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/12_firestarter_transparent_icon.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/02_restart_dhcp3-server.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/02_restart_dnsmasq.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/11_desktop_file.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/06_dot_not_hyphen.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/01_use_gksu.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/09_fix_ip_up.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/02_detect_dhcp3-server_correctly.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/15_update_sv_po.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/10_dhcp_hook.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/14_update_non_routables.dpatch' will not be represented in diff
dpkg-source: warning: executable mode 0755 of 'debian/patches/13_browser_nonroot.dpatch' will not be represented in diff
dpkg-source: warning: ignoring deletion of file firestarter.desktop
dpkg-source: building firestarter in firestarter_1.0.3-6ubuntu2.dsc
dpkg-source: unrepresentable changes to source

```

My question is if/how this change of Icons can be done ?

thanks in advance anyone!

---


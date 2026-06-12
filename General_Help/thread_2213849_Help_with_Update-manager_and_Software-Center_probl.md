---
title: "Help with Update-manager and Software-Center problems"
date: 2014-03-28
forum: General Help
---

### Post by DiscoDave95 on 2014-03-28
Hey I am running Xubuntu 12.04, and when i try to open the Software Center I get an error message that says "Failed to execute command "/usr/bin/software-center %u. Failed to execute child process "/usr/bin/software-center" (No such file or directory)" and the update manager says that an occured.

When I run sudo apt-get update, I receive no errors; so when I ran sudo apt-get update and receive this error.

```
(Reading database ... 575296 files and directories currently installed.)
Preparing to replace python-software-properties 0.82.7.7 (using .../python-software-properties_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/python-software-properties.prerm: 6: /var/lib/dpkg/info/python-software-properties.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-software-properties.postinst: 6: /var/lib/dpkg/info/python-software-properties.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-center 5.2.10 (using .../software-center_5.2.10_all.deb) ...
/var/lib/dpkg/info/software-center.prerm: 6: /var/lib/dpkg/info/software-center.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-center_5.2.10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-center.postinst: 8: /var/lib/dpkg/info/software-center.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-common 0.82.7.7 (using .../software-properties-common_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-common.prerm: 6: /var/lib/dpkg/info/software-properties-common.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-properties-common.postinst: 6: /var/lib/dpkg/info/software-properties-common.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-gtk 0.82.7.7 (using .../software-properties-gtk_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-gtk.prerm: 6: /var/lib/dpkg/info/software-properties-gtk.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-properties-gtk.postinst: 11: /var/lib/dpkg/info/software-properties-gtk.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb
 /var/cache/apt/archives/software-center_5.2.10_all.deb
 /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb
 /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


When i type sudo apt-get install -f i get this error
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 python-configglue python-ubuntuone-client ubuntuone-client mythes-en-au
  elementary-icon-theme linux-headers-3.2.0-52-generic gir1.2-indicate-0.7 linux-headers-3.2.0-52
  ubuntuone-installer language-pack-kde-zh-hans-base compiz-plugins-extra
  python-ubuntuone-storageprotocol hyphen-en-us lubuntu-icon-theme python-pyinotify wine-mono0.0.8
  firefox-locale-zh-hans python-protobuf wine-gecko1.4 wine-gecko1.4:i386 libsyncdaemon-1.0-1
  language-pack-kde-en kde-l10n-engb libubuntuoneui-3.0-1 openjdk-7-jre-lib
  language-pack-zh-hans-base gcc-4.5-base libtommath0 protobuf-compiler kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans language-pack-kde-en-base libprotoc7
  openoffice.org-hyphenation
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/689 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 575296 files and directories currently installed.)
Preparing to replace python-software-properties 0.82.7.7 (using .../python-software-properties_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/python-software-properties.prerm: 6: /var/lib/dpkg/info/python-software-properties.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-software-properties.postinst: 6: /var/lib/dpkg/info/python-software-properties.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-center 5.2.10 (using .../software-center_5.2.10_all.deb) ...
/var/lib/dpkg/info/software-center.prerm: 6: /var/lib/dpkg/info/software-center.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-center_5.2.10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-center.postinst: 8: /var/lib/dpkg/info/software-center.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-common 0.82.7.7 (using .../software-properties-common_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-common.prerm: 6: /var/lib/dpkg/info/software-properties-common.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-properties-common.postinst: 6: /var/lib/dpkg/info/software-properties-common.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-gtk 0.82.7.7 (using .../software-properties-gtk_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-gtk.prerm: 6: /var/lib/dpkg/info/software-properties-gtk.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-properties-gtk.postinst: 11: /var/lib/dpkg/info/software-properties-gtk.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb
 /var/cache/apt/archives/software-center_5.2.10_all.deb
 /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb
 /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Pleae help me, 

Thanks

---

### Post by hansdown on 2014-03-28
Hi DiscoDave95.

Try

> sudo apt-get autoremove

Please post back if any errors occur.

---

### Post by DiscoDave95 on 2014-03-29
i got this error message

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  compiz-plugins-extra elementary-icon-theme firefox-locale-zh-hans gcc-4.5-base
  gir1.2-indicate-0.7 gir1.2-ubuntuoneui-3.0 hyphen-en-us kde-l10n-engb kde-l10n-zhcn
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-zh-hans
  language-pack-kde-zh-hans-base language-pack-zh-hans language-pack-zh-hans-base libprotoc7
  libsyncdaemon-1.0-1 libtommath0 libubuntuoneui-3.0-1 linux-headers-3.2.0-52
  linux-headers-3.2.0-52-generic lubuntu-icon-theme mythes-en-au openjdk-7-jre-lib
  openoffice.org-hyphenation protobuf-compiler python-configglue python-protobuf python-pyinotify
  python-ubuntuone-client python-ubuntuone-storageprotocol ubuntuone-client ubuntuone-installer
  wine-gecko1.4 wine-gecko1.4:i386 wine-mono0.0.8
0 upgraded, 0 newly installed, 36 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/689 kB of archives.
After this operation, 236 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 575296 files and directories currently installed.)
Preparing to replace python-software-properties 0.82.7.7 (using .../python-software-properties_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/python-software-properties.prerm: 6: /var/lib/dpkg/info/python-software-properties.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/python-software-properties.postinst: 6: /var/lib/dpkg/info/python-software-properties.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-center 5.2.10 (using .../software-center_5.2.10_all.deb) ...
/var/lib/dpkg/info/software-center.prerm: 6: /var/lib/dpkg/info/software-center.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-center_5.2.10_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-center.postinst: 8: /var/lib/dpkg/info/software-center.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-common 0.82.7.7 (using .../software-properties-common_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-common.prerm: 6: /var/lib/dpkg/info/software-properties-common.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-properties-common.postinst: 6: /var/lib/dpkg/info/software-properties-common.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace software-properties-gtk 0.82.7.7 (using .../software-properties-gtk_0.82.7.7_all.deb) ...
/var/lib/dpkg/info/software-properties-gtk.prerm: 6: /var/lib/dpkg/info/software-properties-gtk.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/software-properties-gtk.postinst: 11: /var/lib/dpkg/info/software-properties-gtk.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python-software-properties_0.82.7.7_all.deb
 /var/cache/apt/archives/software-center_5.2.10_all.deb
 /var/cache/apt/archives/software-properties-common_0.82.7.7_all.deb
 /var/cache/apt/archives/software-properties-gtk_0.82.7.7_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


Something seems to be seriously wrong here :(

---

### Post by DiscoDave95 on 2014-03-29
Is all hope lost? Am I better off just reinstalling the operating system? I have nothing on this machine anyway. 

I also noticed that /usr/bin/python doesn't exist? Could python of maybe got accidentally uninstalled and caused all these problems? If so I am able to reinstall python and fix all this?

Any help is appreciated, thanks

---


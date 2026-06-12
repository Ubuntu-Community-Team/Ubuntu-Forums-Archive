---
title: "Can't install or remove edubuntu-artwork"
date: 2016-02-04
forum: General Help
---

### Post by Bucky Ball on 2016-02-04
Hi all,

Custom built machine, had it two days, Xubuntu-core 15.10 installed, all working great ... almost.

For this machine, after the core install, I installed Blender, Firefox, Synaptic, VLC, Audacity and not much else. Except edubuntu-artwork because, well, I've always liked it, always do a custom install and always install that somewhere around the beginning. 

This time, I get the first message below when I try to install (it's saying its already the newest version because I can't uninstall it either and adding the extras was a previous attempt at getting it installed properly ... I'd done an autoremove previous to this and guess it was just adding the extras back):

```
bucky@UStudio:~$ sudo apt-get install edubuntu-artwork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
edubuntu-artwork is already the newest version.
The following extra packages will be installed:
  breathe-icon-theme edubuntu-wallpapers elementary-icon-theme
  human-icon-theme light-themes
The following NEW packages will be installed:
  breathe-icon-theme edubuntu-wallpapers elementary-icon-theme
  human-icon-theme light-themes
0 to upgrade, 5 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/24.4 MB of archives.
After this operation, 92.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package human-icon-theme.
(Reading database ... 178499 files and directories currently installed.)
Preparing to unpack .../human-icon-theme_0.36_all.deb ...
Unpacking human-icon-theme (0.36) ...
Selecting previously unselected package breathe-icon-theme.
Preparing to unpack .../breathe-icon-theme_0.51.2_all.deb ...
Unpacking breathe-icon-theme (0.51.2) ...
Selecting previously unselected package light-themes.
Preparing to unpack .../light-themes_14.04+15.10.20151001-0ubuntu1_all.deb ...
Unpacking light-themes (14.04+15.10.20151001-0ubuntu1) ...
Selecting previously unselected package edubuntu-wallpapers.
Preparing to unpack .../edubuntu-wallpapers_15.02.1_all.deb ...
Unpacking edubuntu-wallpapers (15.02.1) ...
Selecting previously unselected package elementary-icon-theme.
Preparing to unpack .../elementary-icon-theme_2.7.1-0ubuntu6_all.deb ...
Unpacking elementary-icon-theme (2.7.1-0ubuntu6) ...
Setting up human-icon-theme (0.36) ...
Setting up breathe-icon-theme (0.51.2) ...
Setting up light-themes (14.04+15.10.20151001-0ubuntu1) ...
Setting up edubuntu-wallpapers (15.02.1) ...
Setting up elementary-icon-theme (2.7.1-0ubuntu6) ...
gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/elementary
dpkg: error processing package edubuntu-artwork (--configure):
 package edubuntu-artwork is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 edubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now try to remove:

```
bucky@UStudio:~$ sudo apt-get remove edubuntu-artwork
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  breathe-icon-theme edubuntu-wallpapers elementary-icon-theme
  human-icon-theme light-themes
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  edubuntu-artwork
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 1,507 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 193834 files and directories currently installed.)
Removing edubuntu-artwork (15.02.1) ...
/var/lib/dpkg/info/edubuntu-artwork.postrm: 31: /var/lib/dpkg/info/edubuntu-artwork.postrm: update-gconf-defaults: not found
dpkg: error processing package edubuntu-artwork (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 edubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And that's where I'm stuck. It's having odd consequences. Everything I try to install ends with an error about edubuntu-artwork, but oddly, most things install while a few do not. I can't install jackd, for instance. :-k

So, rockin' new computer, setting up the audio/visual install, but stuck with a repo and/or dependency mishap. I've checked the sources.list and everything looks normal. I'll post if it gets to that but the solution is probably staring me in the face and I'm not seeing ... hopefully. 

Sometimes it helps to talk about it ... :)

---

### Post by sandyd on 2016-02-04
Maybe try:
```

sudo apt-get install --reinstall edubuntu-artwork
```

---

### Post by Bucky Ball on 2016-02-04
```
bucky@UStudio:~$ sudo apt-get install --reinstall edubuntu-artwork
[sudo] password for bucky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 to reinstall, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/213 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package edubuntu-artwork.
(Reading database ... 193835 files and directories currently installed.)
Preparing to unpack .../edubuntu-artwork_15.02.1_all.deb ...
Unpacking edubuntu-artwork (15.02.1) over (15.02.1) ...
Processing triggers for libglib2.0-0:amd64 (2.46.1-1) ...
Setting up edubuntu-artwork (15.02.1) ...
/var/lib/dpkg/info/edubuntu-artwork.postinst: 18: /var/lib/dpkg/info/edubuntu-artwork.postinst: update-gconf-defaults: not found
dpkg: error processing package edubuntu-artwork (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 edubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks for the suggestion. I tried that via marking for reinstallation in Synaptic previously to no avail also. Still stuck. :|

* Incidentally, when I install anything in Synaptic (or try) I get this at the end:

> E: edubuntu-artwork: subprocess installed post-installation script returned error exit status 127

As I say, most things seem to install fine, though. Just the odd app here and there.

---

### Post by sandyd on 2016-02-05
> **Bucky Ball said:**
> ```
bucky@UStudio:~$ sudo apt-get install --reinstall edubuntu-artwork
[sudo] password for bucky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 to reinstall, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/213 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package edubuntu-artwork.
(Reading database ... 193835 files and directories currently installed.)
Preparing to unpack .../edubuntu-artwork_15.02.1_all.deb ...
Unpacking edubuntu-artwork (15.02.1) over (15.02.1) ...
Processing triggers for libglib2.0-0:amd64 (2.46.1-1) ...
Setting up edubuntu-artwork (15.02.1) ...
/var/lib/dpkg/info/edubuntu-artwork.postinst: 18: /var/lib/dpkg/info/edubuntu-artwork.postinst: **update-gconf-defaults: not found**
dpkg: error processing package edubuntu-artwork (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 edubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks for the suggestion. I tried that via marking for reinstallation in Synaptic previously to no avail also. Still stuck. :|

* Incidentally, when I install anything in Synaptic (or try) I get this at the end:



As I say, most things seem to install fine, though. Just the odd app here and there.

postinstall script seems to be having issues with the fact that it has no update-gconf-defaults to run. looks like some kind of dependency error since it should automatically install that. It seems to be part of the gconf2 package -> [http://packages.ubuntu.com/search?searchon=contents&keywords=update-gconf-defaults&mode=exactfilename&suite=trusty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=update-gconf-defaults&mode=exactfilename&suite=trusty&arch=any)

So,
```

sudo apt-get install gconf2
```

---

### Post by Bucky Ball on 2016-02-05
Thanks for that. No longer getting the edubuntu-artwork errors (they disappeared in the process of installing gconf2 in Synaptics), but something else has cropped up. After I do an update, new message. Hashsum mismatch:

```
Fetched 81.7 kB in 12s (6,444 B/s)                                             
W: Failed to fetch http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/wily-security/universe/source/Sources  Hash Sum mismatch

W: Failed to fetch http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/wily-security/universe/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://mirror.aarnet.edu.au/pub/ubuntu/archive/dists/wily-security/universe/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

I'm diggin' ...

---

### Post by vasa1 on 2016-02-05
I sometimes get errors in the sudo apt-get update process but they go away later. I'm guessing some temporary issue in the servers.

---

### Post by Bucky Ball on 2016-02-05
Well, everything seems to be working faultlessly apart from this message at the end of an update and busy with trying to get some work done on it as I go right now, so will put up with it for the moment (although won't rest until its gone someway) and sniff about some more later. 

Had a look for leads with the hashsum mismatch error earlier, found some things, but nothing that fixed. Then research responsibilities had to take priority (official research ones that is!).

---


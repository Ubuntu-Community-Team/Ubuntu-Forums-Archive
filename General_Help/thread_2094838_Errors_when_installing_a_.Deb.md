---
title: "Errors when installing a .Deb"
date: 2012-12-14
forum: General Help
---

### Post by morbid_bean on 2012-12-14
I am trying to install Steam on my Xubuntu 12.04 

When doubleclicking the icon I get:

```
Deb I get "Could not open 'steam_latest.deb': The package might be corrupt or you are not allowed to open the file. Check the permission of the file."
```

And when running from terminal I get:
```
~/Downloads$ sudo dpkg -i steam_latest.deb
(Reading database ... 137440 files and directories currently installed.)
Unpacking steam (from steam_latest.deb) ...
dpkg-deb (subprocess): short read on buffer copy for failed to write to pipe in copy
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing steam_latest.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/steam/bootstraplinux_ubuntu12_32.tar.xz'
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 steam_latest.deb
```

I have downloadable the file to ensure its not corrupt,  Changed permissions for the file, also ran the following:  **sudo apt-get update**; **sudo apt-get -f**

What can I try next?

---

### Post by Cheesehead on 2012-12-14
This is well explained at [http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/](http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/)

Short answer: The .deb is probably corrupt.
If you have downloaded it twice with the same result both times, then report the issue to the steam packagers.

---

### Post by morbid_bean on 2012-12-15
Well I got it working.  Seems have corrupted the download while on a public WiFi while out.   When I got home it downloaded the deb and installed just fine!

Thanks for the reply

---


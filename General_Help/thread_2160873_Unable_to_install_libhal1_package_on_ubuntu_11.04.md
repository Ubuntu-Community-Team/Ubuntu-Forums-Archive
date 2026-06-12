---
title: "Unable to install libhal1 package on ubuntu 11.04"
date: 2013-07-08
forum: General Help
---

### Post by AJIT ALYANA on 2013-07-08
Hi
        I get the following error while installing libhal1 package on ubuntu 11.04.

apt-get install libhal1

WARNING: The following packages cannot be authenticated!
  libhal1
Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty/universe libhal1 amd64 0.5.14-5+svn1
  404  Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal1_0.5.14-5+svn1_amd64.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/h/hal/libhal1_0.5.14-5+svn1_amd64.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Looks like the package is missing in the specified location.Is there any alternate way to install libhal1 package

---

### Post by BreezyBrooke on 2013-07-08
You know 11.04 is End Of Life and not supported anymore, right? If you computer can handle 11.04 is surely can handle 12.04. Please back up your data and upgrade to 12.04.

As for the missing files, the archive is unmantained, so it's very well likely that things will go wrong on the archive servers.

---

### Post by Impavidus on 2013-07-08
[COLOR=#000000][COLOR=#0000BB][/COLOR][COLOR=#007700][/COLOR][/COLOR]11.04 is end of life. The packages are no longer maintained and have been moved to the old release server: [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)
[COLOR=#000000][COLOR=#FF8000][/COLOR][/COLOR]Some additional reading: [http://ubuntuforums.org/showthread.php?t=1190101](http://ubuntuforums.org/showthread.php?t=1190101)

Alternatively, and recommended, upgrade to a supported version of Ubuntu. Any version &#8805; 12.04 is OK.

---

### Post by BreezyBrooke on 2013-07-08
Impavidus, the person is already on the archive repos.

---

### Post by snowpine on 2013-07-08
The archive repos have been closed permanently, as 11.04 is no longer supported.

---


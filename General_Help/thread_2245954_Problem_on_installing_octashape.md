---
title: "Problem on installing octashape"
date: 2014-09-27
forum: General Help
---

### Post by satimis on 2014-09-27
Hi all,

Ubuntu 14.04 desktop 64bit (VM)
Vertualizer	Oracle VirtualBox

I followed

Octoshape
[https://help.ubuntu.com/community/Octoshape](https://help.ubuntu.com/community/Octoshape)

to install Octoshape

On step 5
Info <!> amd64 users should use: 
&#10219; echo '<e JavaExec="'$(dpkg -L ia32-sun-java6-bin | grep client/libjvm.so)'" />' > ~/Desktop/octoshape/setup.xml```

dpkg-query: package 'ia32-sun-java6-bin' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

Please advise how to install ia32-sun-java6-bin?  Can it work on 64bit?

Thanks

Regards
satimis

---


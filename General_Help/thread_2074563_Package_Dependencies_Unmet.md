---
title: "Package Dependencies Unmet"
date: 2012-10-21
forum: General Help
---

### Post by StevenHodges92 on 2012-10-21
When I try to install wine 1.4 I get the "package dependecies unmet" message and I get these
 
  ```

 The following packages have unmet dependencies:  wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.7ubuntu6 is to be installed          Depends: libc6 (>= 2.14) but 2.15-0ubuntu20 is to be installed          Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1) but 1.4.1-0ubuntu1 is to be installed          Depends: wine1.4-i386 (= 1.4.1-0ubuntu1) but it is not going to be installed 

```I  downloaded synaptic package manager and reinstalled dpkg but it was  already installed and after installing it, it was still on the list when  it failed to install wine, so whats up?

When I try to install the package "wine1.4" it gives me this

```
wine1.4:
 Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1)
 Depends: wine1.4-i386 (=1.4.1-0ubuntu1) but it is not installable
 Recommends: gnome-exe-thumbnailer but it is not going to be installed or
     kde-runtime but it is not going to be installed
 Recommends: ttf-droid
 Recommends: ttf-mscorefonts-installer but it is not going to be installed
 Recommends: ttf-umefont but it is not going to be installed
 Recommends: ttf-unfonts-core but it is not going to be installed
 Recommends: winbind but it is not going to be installed
 Recommends: winetricks but it is not going to be installed


```

In the synaptic package manager, it marks wine1.4-common and wine1.4-smf64 green but puts an exclamation point and red over "wine1.4" so I cant install any of them, what do I do?

---


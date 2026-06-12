---
title: "&#1045;limination of Ristretto"
date: 2013-12-09
forum: General Help
---

### Post by Vukatamayn on 2013-12-09
Hello, Fellows!
I'm using Xubuntu 12.04, installed "Xfce4-Goodies" via Synaptic, but now I want remove only Ristretto without delete "Xfce4-Goodies"! In Synaptic has another package "Ristretto" and when choose to remove, receive message: "Will be removed "Xfce4-Goodies""!

[B]How to remove Ristretto without delete "Xfce4-Goodies"? Or how to have "Xfce4-Goodies" without Ristretto?

Tnx![/B]

---

### Post by vasa1 on 2013-12-09
> **Vukatamayn said:**
> Hello, Fellows!
I'm using Xubuntu 12.04, installed "Xfce4-Goodies" via Synaptic, but now I want remove only Ristretto without delete "Xfce4-Goodies"! In Synaptic has another package "Ristretto" and when choose to remove, receive message: "Will be removed "Xfce4-Goodies""!

[B]How to remove Ristretto without delete "Xfce4-Goodies"? Or how to have "Xfce4-Goodies" without Ristretto?

Tnx![/B]

From your terminal, run **apt-cache show xfce4-goodies**. Look at the output. You should see this near the bottom:
>  This is a metapackage to ease upgrades, installations, and provide a
 consistent upgrade path from previous versions. It can safely be removed with
 no ill effects.


---

### Post by Buntu Bunny on 2013-12-09
> **vasa1 said:**
> From your terminal, run **apt-cache show xfce4-goodies**. Look at the output. You should see this near the bottom:

> This is a metapackage to ease upgrades, installations, and provide a
consistent upgrade path from previous versions. It can safely be removed with
no ill effects. 



But does the OP want to remove the metapackage, i.e. Xfce4-Goodies? Sounds like he wants to keep all the goodies except Ristretto.

---

### Post by qamelian on 2013-12-09
Removing the metapackage does not remove the packages included in the metapackage. That's why you can remove ubuntu-desktop without breaking your system.

---

### Post by vasa1 on 2013-12-09
> **Buntu Bunny said:**
> But does the OP want to remove the metapackage, i.e. Xfce4-Goodies? Sounds like he wants to keep all the goodies except Ristretto.
+1 to what qamelian said.

I really like *apt-cache show package_name* and *apt-cache showpkg package_name*. I'm sure there are other ways of doing things and people could convert this into an apt versus aptitude versus synaptic versus software center religious war, but that aside ...

Let's look at the package *ristretto* using the two apt-cache commands.

```
[08:48 AM] ~ $ apt-cache show ristretto
Package: ristretto
Priority: extra
Section: **universe**/graphics
Installed-Size: 1147
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>
Architecture: amd64
Version: 0.6.3-2
**Depends**: libc6 (>= 2.4), libcairo2 (>= 1.8.0), libdbus-glib-1-2 (>= 0.78), libexif12, libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.35.9), libgtk2.0-0 (>= 2.18.0), libpango1.0-0 (>= 1.14.0), libx11-6, libxfce4ui-1-0 (>= 4.9.0), libxfce4util6 (>= 4.9.0), libxfconf-0-2 (>= 4.6.0)
Recommends: tumbler
Filename: pool/universe/r/ristretto/ristretto_0.6.3-2_amd64.deb
Size: 243932
MD5sum: ec3438b2e835bc9af676bc75a26a2013
SHA1: 3fcb6b3a8e38edc48ba1366abc86599602ff6977
SHA256: ccd07dcf3231d58ab4968c431e9354f0398c3183b3ca39dccb667385a596bebe
Description-en: lightweight picture-viewer for the Xfce desktop environment
 Ristretto is a fast and lightweight picture-viewer for the Xfce desktop
 environment.
Description-md5: 99d1eb901a80a6f11af6489eb7ae9121
Homepage: http://goodies.xfce.org/
Description-md5: 99d1eb901a80a6f11af6489eb7ae9121
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
**Task**: xubuntu-desktop, ubuntustudio-desktop

[08:49 AM] ~ $ 
```I've bolded a few things and according to my understanding ...
[list][*]**Universe** tells us that *ristretto* is not in main with all that that implies for support
[*]**Depends** lists the other packages required for *ristretto* to function. Note that *xfce4-goodies* isn't listed.
[*]**Task** tells us that *ristretto* is supplied (by default) with two DEs, *xubuntu* and *ubuntustudio*.
[/LIST]
```
[08:49 AM] ~ $ apt-cache showpkg ristretto
Package: ristretto
Versions: 
0.6.3-2 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-amd64_Packages
                  MD5: 99d1eb901a80a6f11af6489eb7ae9121
 Description Language: en
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_saucy_universe_i18n_Translation-en
                  MD5: 99d1eb901a80a6f11af6489eb7ae9121


**Reverse Depends**: 
  ristretto:i386,ristretto
  xubuntu-desktop,ristretto
  xfce4-goodies,ristretto
  ubuntustudio-desktop,ristretto
  hamexam,ristretto
  fccexam,ristretto
Dependencies: 
0.6.3-2 - libc6 (2 2.4) libcairo2 (2 1.8.0) libdbus-glib-1-2 (2 0.78) libexif12 (0 (null)) libgdk-pixbuf2.0-0 (2 2.22.0) libglib2.0-0 (2 2.35.9) libgtk2.0-0 (2 2.18.0) libpango1.0-0 (2 1.14.0) libx11-6 (0 (null)) libxfce4ui-1-0 (2 4.9.0) libxfce4util6 (2 4.9.0) libxfconf-0-2 (2 4.6.0) tumbler (0 (null)) ristretto:i386 (0 (null)) 
Provides: 
0.6.3-2 - 
Reverse Provides: 
[09:04 AM] ~ $ 
```What's of interest here is the section on **Reverse Depends**. It tells us that ristretto will be pulled in (by default) if we install any of the packages listed first in each line.

I've mentioned "by default" twice. Depending on the situation, it's possible to avoid installing certain "dependencies" by using the *--no-install-recommends* switch with *sudo apt-get install*. For example, I ran *sudo apt-get install --no-install-recommends xubuntu-desktop* on my Lubuntu 13.10 installation and *ristretto* wasn't installed.

---

### Post by Dennis N on 2013-12-09
> **Vukatamayn said:**
> Hello, Fellows!
I'm using Xubuntu 12.04, installed "Xfce4-Goodies" via Synaptic, but now I want remove only Ristretto without delete "Xfce4-Goodies"! In Synaptic has another package "Ristretto" and when choose to remove, receive message: "Will be removed "Xfce4-Goodies""!

[B]How to remove Ristretto without delete "Xfce4-Goodies"? Or how to have "Xfce4-Goodies" without Ristretto?

Tnx![/B]

You can test the removal with the simulation **apt-get -s remove ristretto** (do not use sudo) and see what packages will be removed. Removing xfce4-goodies removes no software since it is a metapackage as others have mentioned. So you will have the rest of the goodies left without ristretto when done.

My simulation below doesn't mention xfce4-goodies, as that package is not present on my xubuntu 12.04. 

In my case, what is removed is in red.

```
dn@Alexa:~$ apt-get -s remove ristretto
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-52-generic linux-headers-3.2.0-55-generic
  linux-headers-3.2.0-51 linux-headers-3.2.0-52 linux-headers-3.2.0-53
  linux-headers-3.2.0-54 linux-headers-3.2.0-55 libreoffice-emailmerge
  linux-headers-3.2.0-53-generic linux-headers-3.2.0-51-generic
  linux-headers-3.2.0-54-generic
Use 'apt-get autoremove' to remove them.
[COLOR="#FF0000"]The following packages will be REMOVED:
  ristretto
0 upgraded, 0 newly installed, 1 to remove[/COLOR] and 7 not upgraded.
[COLOR="#FF0000"]Remv ristretto [0.3.6-0ubuntu1][/COLOR]


```

---

### Post by Buntu Bunny on 2013-12-10
An interesting and useful discussion. I've learned some things here. Thanks all.

---


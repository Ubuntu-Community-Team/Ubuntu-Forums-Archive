---
title: "libgimp2.0-dev broken"
date: 2016-11-18
forum: General Help
---

### Post by danielsender on 2016-11-18
Hi,

I'm running 16.04 on a Dell M90. I wanted to compile a gimp plugin and for that purpose the package **libgimp2.0-dev** is required (headers and other files). However, when I try to install it comes back with the **Status** field as broken. I was wondering if there is any known fix for this.

Thanks,

Daniel

---

### Post by SeijiSensei on 2016-11-18
Are you sure you have the right architecture?

i386: [https://launchpad.net/ubuntu/xenial/i386/libgimp2.0-dev/2.8.16-1ubuntu1](https://launchpad.net/ubuntu/xenial/i386/libgimp2.0-dev/2.8.16-1ubuntu1)
amd64: [https://launchpad.net/ubuntu/xenial/amd64/libgimp2.0-dev/2.8.16-1ubuntu1](https://launchpad.net/ubuntu/xenial/amd64/libgimp2.0-dev/2.8.16-1ubuntu1)

---

### Post by danielsender on 2016-11-18
by architecture do you mean 32b or 64b? I have the latter. I attempted the installation through synaptic, so I assume that he knows what package to download.

---

### Post by mc4man on 2016-11-18
Try from command line, maybe it'll be informative
sudo apt install libgimp2.0-dev

Have you used a ppa for gimp?, if so then that's probably the source of your issue.

---

### Post by danielsender on 2016-11-18
No, I don't have the gimp PPA, I prefer to stick to the Ubuntu's. In any case, using apt-get shows the following:
```
sudo apt-get install libgimp2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgimp2.0-dev : Depends: libgtk2.0-dev (>= 2.12.5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So I attempted to follow the dependency chain to install and they all showed similar messages. I'm sure I'm not the only one on 16.04 who is seeing this.

---

### Post by mc4man on 2016-11-18
Install aptitude & try with it instead of apt. It's usually more verbose as to the problem. You could just as well try on libgtk2.0-dev as that's what's pulling in a lot of the deps.

---

### Post by SeijiSensei on 2016-11-18
Have you run a dist-upgrade lately?  Maybe the headers don't match the kernel code.  Try
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install libgimp2.0-dev libgtk2.0-dev

```
dist-upgrade may offer to install a lot of stuff depending on how long it's been since you've last run one.  I've never had a problem simply accepting the proposed list of packages myself.  You'll probably get a new kernel and need to reboot.

---

### Post by danielsender on 2016-11-19
Trying to install simultaneously libgimp2.0-dev and libgtk2.0-dev led me to another bunch of dependency errors. This is the screen of aptitude on libgimp2.0-dev:
```
         Packages             libgimp2.0-dev infolibgimp2.0-dev info
aptitude 0.7.4
  Section: universe/libdevel
  Maintainer: Ubuntu Developers
<ubuntu-devel-discuss@lists.ubuntu.com>
  Architecture: amd64
  Compressed Size: 85.7 k
  Uncompressed Size: 1,888 k
  Source Package: gimp
  --\ Depends (5)
    --- libc6 (>= 2.4)
    --- libgimp2.0 (= 2.8.16-1ubuntu1)
    --- libglib2.0-0 (>= 2.30.2)
    --- libgtk2.0-dev (>= 2.12.5) (UNSATISFIED)
    --- pkg-config
  --\ Suggests (1)
    --- libgimp2.0-doc (UNSATISFIED)
  --\ Conflicts (1)
    --- libgimp2.0-dev
  --- Packages which depend on libgimp2.0-dev (3)
  --\ Versions of libgimp2.0-dev (1)
p    2.8.16-1ubuntu1

```

Thanks.

---

### Post by mc4man on 2016-11-19
As said I'd look at what aptitude says about libgtk2.0-dev as if you can get it to install then libgimp2.0-dev would install.
Also it appears you either don't have xenial-security & xenial-updates enabled or your repo mirror is deficient. Check in Software & Updates > Updates tab. (- current version for libgimp is 2.8.16-1ubuntu1.1

---

### Post by danielsender on 2016-11-19
```
 Actions  Undo  Package  Resolver  Search  Options  Views  HelpC-T: Menu  ?: Help  q: Quit  u: Update  g: Preview/Download/Install/Remove Pkgs
         Packages             libgtk2.0-dev info        Resolve Dependencies
aptitude 0.7.4     #Broken: 50  Will use 140 MB of disk space  DL Size: 27.7 MB
--\ Not Installed Packages (2)
  --\ libdevel - Development files for libraries (2)                            
    --\ main - Fully supported Free Software. (2)
pB    libgtk2.0-dev                      +19.5 MB  <none>         2.24.30-1ubunt
pB    libgtk2.0-dev:i386                 +17.4 MB  <none>         2.24.30-1ubunt








Packages in the 'libdevel' section contain files required for building programs&#9618;
that use libraries in the 'libs' section.  You don't need packages from this   &#9618;
section unless you want to compile software yourself.                          &#9618;
                                                                               &#9618;
This group contains 2 packages.                                                &#9618;
                                                                               &#9618;
If you select a package, an explanation of its current state will appear in    &#9618;
this space.                                                                    &#9618;
                                                                               &#9618;
[1(1)/...] Suggest 44 keeps
e: Examine  !: Apply  .: Next  ,: Previous

 Actions  Undo  Package  Resolver  Search  Options  Views  Help
C-T: Menu  ?: Help  q: Quit  u: Update  g: Preview/Download/Install/Remove Pkgs
    Packages    libgtk2.0-dev inlibgtk2.0-dev inlibgtk2.0-dev inResolve Dependen
  --\ Keep the following packages at their current version:                     
    gir1.2-atk-1.0:i386                                                 [UNINST]
    gir1.2-gtk-2.0:i386                                                 [UNINST]
    gir1.2-pango-1.0:i386                                               [UNINST]
    libatk1.0-dev:i386                                                  [UNINST]
    libc6-dev:i386                                                      [UNINST]
    libcairo2-dev                                                       [UNINST]
    libcairo2-dev:i386                                                  [UNINST]
    libexpat1-dev                                                       [UNINST]




















[1(1)/...] Suggest 44 keeps
e: Examine  !: Apply  .: Next  ,: Previous






```

how do I enable xenial-security and xenial-updates? Can you please explain what is a "deficient" a repo mirror?

Thanks.

---

### Post by mc4man on 2016-11-19
I can't make good sense out of what you're pasting from aptitude, seem truncated left to right & up/down
Likely the issue is you have several i386 packages installed so to install libgtk2.0-dev it needs to install libgtk2.0-dev:i386  & probably some dep(s) of libgtk2.0-dev:i386 can not be installed along side of the amd64 package(s)

So in other words it seems  that libgtk2.0-dev & libgtk2.0-dev:i386 cannot be installed at the same time. Your best bet is to remove the conflicting i386 packages..

---

### Post by danielsender on 2016-12-01
Sorry guys, I had to interrupt because I was out of town.

I never used aptitude, so most likely I didn't paste the right info.

If the problem is an issue of i386 and amd64 packages I don't know why that happened. Whenever I install a package I don't specify any architecture so I assume that either apt-get or synaptic would know what version to get.

I manually tried going through the hierarchy of troubled packages and re-install but I'm afraid that is not the right way of fixing the problem. In other words, is there an automatic way of removing and reinstalling all the packages to get the problem fixed?

Thanks.

---

### Post by danielsender on 2016-12-03
This is driving me nuts. I tried the following:
```
sudo aptitude install libgimp2.0-dev
The following NEW packages will be installed:
  libcairo2-dev{a} libexpat1-dev{ab} libfontconfig1-dev{ab} libgimp2.0-dev 
  libgtk2.0-dev{a} libharfbuzz-dev{ab} libharfbuzz-gobject0{a} 
  libpango1.0-dev{a} libxft-dev{a} 
0 packages upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,570 kB of archives. After unpacking 30.5 MB will be used.
The following packages have unmet dependencies:
 libexpat1-dev : Depends: libexpat1 (= 2.1.0-7) but 2.1.0-7ubuntu0.16.04.2 is installed.
 libfontconfig1-dev : Depends: libfontconfig1 (= 2.11.94-0ubuntu1) but 2.11.94-0ubuntu1.1 is installed.
 libharfbuzz-dev : Depends: libharfbuzz0b (= 1.0.1-1build2) but 1.0.1-1ubuntu0.1 is installed.
                   Depends: libharfbuzz-icu0 (= 1.0.1-1build2) but 1.0.1-1ubuntu0.1 is installed.
The following actions will resolve these dependencies:


     Keep the following packages at their current version:
1)     libcairo2-dev [Not Installed]                      
2)     libexpat1-dev [Not Installed]                      
3)     libfontconfig1-dev [Not Installed]                 
4)     libgimp2.0-dev [Not Installed]                     
5)     libgtk2.0-dev [Not Installed]                      
6)     libharfbuzz-dev [Not Installed]                    
7)     libpango1.0-dev [Not Installed]                    
8)     libxft-dev [Not Installed]                         






Accept this solution? [Y/n/q/?]
```
Why is aptitude telling me that a solution is to "Keep the following packages at their current version" when these packages are not installed?
So if I say "Y" I get:
```
No packages will be installed, upgraded, or removed.0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

What am I reading wrong here?

---

### Post by mc4man on 2016-12-03
Solely looking at the aptitude result it's telling you that you no  longer have the Updates and Security repos enabled.  So open Software & Updates, under the Updates tab make sure both are enabled, reload your sources & try again.
(- if both were already enabled then use a different sources mirror..

---

### Post by danielsender on 2016-12-03
You saved me from a lot of grief!!! That was the problem. Thank you very, very much.

Cheers,

Daniel

---


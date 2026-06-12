---
title: "Gwenviews cant access external hard drive."
date: 2019-03-17
forum: General Help
---

### Post by 007casper on 2019-03-17
Ubuntu software section has two gwenviews. 

I have loaded the older version first, which is "4:17.12.3-0ubuntu1" and it was able to read the contents of my external hard drive.  The source of the application was ubuntu-bionic-universe.

Then, I have realized the second version of the gwenview, which is 18.12.2. This version is the most updated version of the gwenview. The source of the application is Snap Store. However, when I load this current version, it cant read or access the external hard drive at all.

in one of the reviews for the older vesion, I have read that if it cant read a directory to add lib's first. I have done that, and hoped that it will fix the issue with 18.12.2.  
```
sudo apt-get install kio kinit kdelibs-bin kded5
```

However, it still cant read the external hard drive.

I get Error - Could not enter folder /media/x/ I have also tried /media/ same error.

When I hit root, it goes to that directory. However, cant access media folder.

on terminal when I do / ls -al
media is 
drwxr-xr-x root root media
drwxr-x---+ root root x
drwxrwxrwx 1 x x 'My Externaldrive'

ubuntu version is 18.04.2 LTS

Please, advise. Thank you.

---

### Post by TheFu on 2019-03-17
Many snaps have restricted access to external storage.  I have no idea how to solve it and keep using a snap.  You can remove it using snap remove.  You can read more about snaps at [https://snapcraft.io/](https://snapcraft.io/)

I think they may become a good package deployment solution, someday. Today snaps seem premature for most production use unless the app is 100% standalone and didn't need access to addon libraries or data files.

---

### Post by 007casper on 2019-03-17
How can I find the latest stable release .deb for gwenview?

[https://userbase.kde.org/Gwenview](https://userbase.kde.org/Gwenview) 
the above link doesnt have a download button

[https://packages.ubuntu.com/bionic/graphics/gwenview](https://packages.ubuntu.com/bionic/graphics/gwenview)
list older version... it does have source files for 

    [gwenview_17.12.3-0ubuntu1.dsc]
    [gwenview_17.12.3.orig.tar.xz]
    [gwenview_17.12.3-0ubuntu1.debian.tar.xz]

[https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/gwenview_17.12.3-0ubuntu1_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/gwenview_17.12.3-0ubuntu1_amd64.deb.html)
lists 17.12.3 also

cant seem to locate .deb file for the latest stable version 18.12.3

I am little bit confused about what snap remove does...

what is the best way to load the current stable version? I have loaded 17.12.30ubuntu1 deb file which is able to access the external drive.
However, I really would like to use the latest version. Please, advise.

Thank you so much.

---

### Post by deadflowr on 2019-03-18
Try connecting the snap to the removable-media interface
```
sudo snap connect gwenview:removable-media
```

---

### Post by TheFu on 2019-03-18
> **007casper said:**
> How can I find the latest stable release .deb for gwenview?

[https://userbase.kde.org/Gwenview](https://userbase.kde.org/Gwenview) 
the above link doesnt have a download button

[https://packages.ubuntu.com/bionic/graphics/gwenview](https://packages.ubuntu.com/bionic/graphics/gwenview)
list older version... it does have source files for 

    [gwenview_17.12.3-0ubuntu1.dsc]
    [gwenview_17.12.3.orig.tar.xz]
    [gwenview_17.12.3-0ubuntu1.debian.tar.xz]

[https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/gwenview_17.12.3-0ubuntu1_amd64.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-amd64/gwenview_17.12.3-0ubuntu1_amd64.deb.html)
lists 17.12.3 also

cant seem to locate .deb file for the latest stable version 18.12.3

I am little bit confused about what snap remove does...

what is the best way to load the current stable version? I have loaded 17.12.30ubuntu1 deb file which is able to access the external drive.
However, I really would like to use the latest version. Please, advise.

Thank you so much.

a) If you don't absolutely need the newest version, stick with the version that is part of a Canonical repo. These are patched and maintained for security issues.
b) If you do absolutely need a newer version, there are 4 *possible* choices, not all of them will be available.

b1) Find a PPA from a respected place, add that to your APT DB. Use it just like a Canonical repo. If the PPA maintainer is respectable, that team will maintain it for compatibility, security patching, and updates for the commonly released Ubuntu LTS and current short-term support releases. apt update/apt upgrade processes continue to work and are fully integrated with other GUIs for package management on Ubuntu.

b2) Learn to use snaps and overcome any shortcomings.  See link provided. Snaps have an upgrade method similar to APT. I don't know how to get it invoked, but it is 1-2 commands just like APT.

b3) Find a .deb file produced directly from the project team. There are liabilities in using .deb files.  Linux isn't like Windows.  When you manually load a .deb file, you are telling APT that you will manually handle dependencies.  Doing this means that APT may hold back other libraries and programs which need to be updated.  Expect to have to manually install any newer versions of the .deb file every few weeks.  Manually keep track somewhere - WRITE IT DOWN - any files you install this way, be cause in 3-6 months, there are likely to be dependency issues which break your Ubuntu/Debian/Other APT-base install.  This does not fully integrate into the normal apt update/apt upgrade package maintenance.

b4) Find the source for the project, all dependencies, and setup a build environment.  Manually build the dependencies, in the correct order, then build the program.  Learning to do this is difficult if you aren't fluent in the specific language and build tools used by that specific project.  A python programmer will have trouble learning to compile and link a complex C/Java project.  There is usually either a README or INSTALL file included in the source code. These are highly variant in quality.   A very small C project might only have a Makefile and a file.c file.  Most projects will have 10+ files spread across a few directories that need to be build in the correct order.  If it isn't obvious, this method don't integrate with any package management system and you will need to pull new code every few weeks to stay current, get bug fixes, and security fixes.  Code is often available at places like gitlab, github, or in tgz or zip files from the developers personal website.

I wouldn't touch b3 or b4 methods these days. In the 1990s, I did the b4 method many times a week because that was the only method available to get most software that wasn't Unix infrastructure code.

I see that deadflowr provided a technique to alter the permissions for a snap container. Very encouraging, though certain programs should probably include commonly needed connections or ask which to allow at installation. [https://docs.snapcraft.io/interface-management/6154](https://docs.snapcraft.io/interface-management/6154)  I may need to give snaps another try on my more powerful systems.  They don't have a place on my limited systems - memory is not unlimited for many people.

---

### Post by 007casper on 2019-03-18
Thank you so much for all your input.  Extremely helpful.

I think I will give "17.12.30ubuntu1" a try, way better than version "4:17.12.3-0ubuntu1"

I am able to access the external hard drive with 17.12.3. However, when I rate pictures, the rating stars dont show up.  It is just a 50% percent gray box without any stars in it.
When I want to filter the images by rating, I still have the same problem.  The stars icon doesnt render at all.

I have a lot of dng (raw pictures) to go through for a project, so to be able to rate images necessary.

I had the same problem, when I loaded 18.12.3. That version didnt render the stars either when I tested with internal hard drive.

What is the best way to solve this problem? Maybe I am just missing the star icon, or I am speculating the icon became corrupted during install.

Please, let me know how to trouble shoot the star icon rating problem. Thank you so much.

---


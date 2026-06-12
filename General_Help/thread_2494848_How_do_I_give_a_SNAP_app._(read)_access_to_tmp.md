---
title: "How do I give a SNAP app. (read) access to /tmp?"
date: 2024-01-29
forum: General Help
---

### Post by davehk on 2024-01-29
The latest version of Libre Office provided in Ubuntu Software is a SNAP. This means that it cannot open files when, for example, you double click on an attachment to an email in Thunderbird. It says that the file does no exist (though it shows the correct file name). The file is indeed where it is supposed to be.

I thought I read somewhere about how to give SNAP  access outside ~ but I can't fine it now, any help would be appreciated.

Thanks

EDIT: from what I've been able to find, this can't be done. I wonder if there is any way to make Thunderbird use a temp directory in /home/[user]?

---

### Post by davehk on 2024-01-29
Solution: scrap the snap version and install using the libreoffice PPA.

---

### Post by TheFu on 2024-01-29
> **davehk said:**
> Solution: scrap the snap version and install using the libreoffice PPA.

Yep.  The answer is you cannot. 

Snap constraints are hard coded and only if the snap packager allows it, can you ask for a snap program constraint to allow access to either /media/ or /mnt/ areas, but nowhere else outside /home/{username} are allowed.  The snap team has known about this poor design choice since at least 2017 and has ignored it.  
The command has the format of:
```
snap connect **chromium**:removable-media
```
removable-media is super secret code for /mnt/ and /media/.  Again, the snap packager has to allow this to be enabled.
Just determine the name of the snap package  (snap list) and replace the "chromium" above with other name.  This won't provide access to /tmp/ unfortunately.

Further, if your HOME directory isn't in /home/{username} snaps won't work at all. Again, the snap team decided to hard code that location pattern, though using /home/ for home directories isn't how enterprises with large numbers of users setup their systems.  It is a failure in the snap design, IMHO.

---

### Post by Dennis N on 2024-01-29
> The latest version of Libre Office provided in Ubuntu Software is a SNAP
You didn't say what release of Ubuntu you are using, but in 23.10 the .deb can be installed from the App Center. All you have to do is switch the selector to "Debian Packages". See Screenshot.

Also, note you can install just the L.O. application(s) you want, not the entire suite.

---

### Post by ian-weisser on 2024-01-29
> **davehk said:**
> [Snap LibreOffice] cannot open files when, for example, you double click on an attachment to an email in Thunderbird. 

It's a known bug: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1881603](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1881603)

---

### Post by Norm24 on 2024-01-29
You can also download the .deb package directly from the Libre Office website.

---

### Post by TheFu on 2024-01-29
> **Norm24 said:**
> You can also download the .deb package directly from the Libre Office website.

Many deb packages will break the package management system in a few months. Just yesterday, at my LUG we spent 45 minutes helping someone that was unable to upgrade for about a month because a .deb package was installed and it was holding a much of core packages, libc, back.  So, if you do install using a .deb file, be certain to write that down so when your package manager refuses to update in a few months, you can remove the deb-package, perform the updates, then go and see if a newer version of that .deb file is available and install it.

By installing .deb files directly, you've told the package management system that you will be responsible for dependency management. This means that you'll need to manually update that .deb file about once a month.

The less hassle method would be to use a PPA or run a version of the software that is already in the Canonical Repos.

I understand that some .deb packages will automatically add their PPA to your system.  I've never seen that myself, but it certainly is possible, just don't count on it.

---

### Post by l3modz on 2024-01-29
PPA libreoffice OR #apt-get install libreoffice was more cool at console/Terminal Ubuntu.

---

### Post by grahammechanical on 2024-01-29
> The latest version of Libre Office provided in Ubuntu Software is a SNAP

I am running 2404 LTS (development version). My installed Libreoffice is a deb. But this install is an upgrade from 22.10. Interestingly, Ubuntu Software does offer to install the snap versions of Ubuntu but it also records the installed deb version.

At the Libreoffice page (Ubuntu Software) there is a panel showing the Source of the package. Does the drop down menu not include the deb version? I have been trying to install the latest 24.04 LTS ISO image on an external SATA drive but the install fails. So, I do not know if the installed Libreoffice of 24.04 LTS will be a snap app. I think it will.

Regards

---

### Post by TheFu on 2024-01-29
grahammechanical, are you certain the DEB package isn't isn't a fake front end to install the snap?  

Like they did with firefox, chromium, lxd and a few other packages?

---

### Post by #&amp;thj^% on 2024-01-29
Mine:
```
apt policy libreoffice-base-core
libreoffice-base-core:
  Installed: 4:24.2.0~rc1-0ubuntu1
  Candidate: 4:24.2.0~rc1-0ubuntu1
  Version table:
 *** 4:24.2.0~rc1-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status

```

NOTE I'm a snap free user.

---

### Post by grahammechanical on 2024-01-29
> grahammechanical, are you certain the DEB package isn't isn't a fake front end to install the snap?  


I do not know. I only know that Ubuntu Software Lists Libreoffice as the deb package installed. And then there is this:

> graham@UbuntuDev:~$ apt policy libreoffice-base-core
libreoffice-base-core:
  Installed: 4:24.2.0~rc1-0ubuntu1
  Candidate: 4:24.2.0~rc1-0ubuntu1
  Version table:
 *** 4:24.2.0~rc1-0ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) noble/main amd64 Packages
        100 /var/lib/dpkg/status

Funny things happen on a rolling type development version that has had online upgrades from a Ubuntu version that did not install snap versions by default. This particular install of 24.04 seems to have both the deb and snap versions of Thunderbird installed. Both snap refresh and apt upgrade actually upgrade Thunderbird.

When I succeed on installing the 24.04 ISO I can test whether the default FULL install actually installs Snap versions of Libreoffice. I know it will install the snap version of Firefox and I guess it will install the snap version of Thunderbird. 

My worry about the snap version of Libreoffice is that it might not access my Libreoffice files on a specific data partition. Only if those files that are in the standard Documents folder will they be accessed by A snap version of Libreoffice. This is my suspicion.

Years ago when Canonical was working on a phone OS it had the idea of something it called a media hub. It was a utility that would allow a user to give applications access to folders that were not in the default Home folder. But nothing came of it.

P.S. This might prove useful:

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

Regards

---

### Post by TheFu on 2024-01-29
> **grahammechanical said:**
>  
Years ago when Canonical was working on a phone OS it had the idea of something it called a media hub. It was a utility that would allow a user to give applications access to folders that were not in the default Home folder. But nothing came of it.

P.S. This might prove useful:

Yes. A permissions and connection manager for Android would be excellent.  Or better, let me specify the types of data files to which each program should have access, so I didn't need to worry about directory locations so much.

Every time I'm on android and my audiobook player can't access nextcloud synchronized files under the Nextcloud data area, I think google lost their mind with all the security.  

The audiobook application doesn't need any special permissions, so there isn't any permissions management for it possible.  The only workaround I've found to provide access to nextcloud data is to use the Nextcloud app and "Export" each file.  They get moved to the Downloads directory and I manually move them to an audiobook directory.  What a pain.  If I didn't love that audiobook player, it wasn't 100% F/LOSS, and it didn't come ad-free, I'd have already found a different app.  I don't want to blame Nextcloud, because sometimes there are files under control of it that shouldn't be accessible by any other programs, but that is rare - it isn't like viewing or editing any file type is what Nextcloud is good at.  Even their "Notes" tool, which has a separate App on Android basically sucks.

Of course, sometimes it is just easier to pull the microSD out, connect it to a computer and use rsync to push all the files over - but it shouldn't be.

I really dislike that almost all of Googles apps require data off the internet to work. It is like they don't want us using local storage at all.  Took me 3 days to realize that the built-in music player wouldn't/couldn't play a local directory.  I'd have purged it if I could. Useless. Completely useless.  Google is in cahoots with network providers to force everything to be streamed from the internet and so many people accept it as the way it should be.  Cough. Sigh.

And then Canonical decides that snaps shouldn't have access to /tmp/ or any arbitrary data location?  What are they smoking?  Sure, make the admin specify, but don't make it impossible.

---


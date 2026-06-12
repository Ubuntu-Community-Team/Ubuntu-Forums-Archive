---
title: "Software updater: failedto download respository information"
date: 2017-02-04
forum: General Help
---

### Post by boatcat on 2017-02-04
Hi all, 

looking for some help with my software updater. It used to work fine but now every time I look for updates it says it cannot download repository information. I'm also having some problems with my laptop waking up from sleep and battery drain issues. Not sure if these are linked.

I'm on 16.04 gnome.

Thanks!

---

### Post by Perfect Storm on 2017-02-04
Can you please post the terminal output, it will make it easier to help.
```
sudo apt-get update
```

Also 'laptop waking up from sleep and battery drain issues' is not related and you may start a different thread for this issue.

---

### Post by boatcat on 2017-02-04
Hi, 

Sure, but I'm afraid I'm very inexperienced with ubuntu. What should I type in to get the relevant info?

Thanks for you help.

---

### Post by boatcat on 2017-02-04
Sorry ignore, the above. I was little confused as I hadn't done the software update via terminal originally, but through the 'app', brain clearly not working today.

here you go

```
Ign:1 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial InReleaseHit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Hit:5 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:8 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Ign:10 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial Release    
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB] 
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Hit:16 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                          
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Hit:21 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Err:11 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:12 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main i386 Packages
Ign:15 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main all Packages
Ign:17 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en_GB
Ign:18 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main Translation-en
Ign:19 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:20 [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 306 kB in 2s (120 kB/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/colingille/freshlight/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: [https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:](https://download.01.org/gfx/ubuntu/16.04/main/dists/xenial/InRelease:) Signature by key 09D6EF97BFB38E916EF060E756A3DEF863961D39 uses weak digest algorithm (SHA1)
E: Failed to fetch [http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/colingille/freshlight/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by howefield on 2017-02-04
There is no xenial repository available for the freshlight ppa, you are basically querying a non existent repository.

Open up the Software & Updates application and from the Other Software tab highlight and delete any reference to the colingille/freshlight/ ppa, close out and you'll be asked to reload your sources, accept and post back any errors, if any.

---

### Post by boatcat on 2017-02-04
fantastic, so simple. Thanks both!

---


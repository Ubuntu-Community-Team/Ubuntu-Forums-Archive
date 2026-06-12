---
title: "How to install Shotcut, lastest version"
date: 2022-03-27
forum: General Help
---

### Post by satimis on 2022-03-27
Ubuntu 20.04

Please advise how to install the latest version of Shotcut ?
**[COLOR="#FF0000"]Not running Snap/flatpak nor using AppImage[/COLOR]**

Shotcut latest version - 21.06.29 

$ sudo add-apt-repository ppa:haraldhv/shotcut```

...
...
Get:14 http://hk.archive.ubuntu.com/ubuntu focal-backports InRelease [108 kB]
Get:15 http://hk.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [278 kB]
Get:16 http://hk.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [390 kB]
Get:17 http://hk.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:18 http://hk.archive.ubuntu.com/ubuntu focal-backports/main amd64 DEP-11 Metadata [7,996 B]
Get:19 http://hk.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [30.8 kB]
Reading package lists... Done                                             
E: The repository 'http://ppa.launchpad.net/haraldhv/shotcut/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Thanks in advance.

Regards

---

### Post by ActionParsnip on 2022-03-27
[http://ppa.launchpad.net/haraldhv/shotcut/ubuntu/dists/](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu/dists/)

The PPA doesn't support Focal and should be removed. Not all PPAs support all releases of Ubuntu.

What is in the new version of the application that you need so very badly? Why is the latest version required?

---

### Post by satimis on 2022-03-27
> **ActionParsnip said:**
> [http://ppa.launchpad.net/haraldhv/shotcut/ubuntu/dists/](http://ppa.launchpad.net/haraldhv/shotcut/ubuntu/dists/)

The PPA doesn't support Focal and should be removed. Not all PPAs support all releases of Ubuntu.

What is in the new version of the application that you need so very badly? Why is the latest version required?

I just found;

Shotcut - New Version 21.06.29
[https://shotcut.org/blog/new-release-210629/](https://shotcut.org/blog/new-release-210629/)

the latest version.

What is the version of Shotcut on Ubuntu repo?

Regards

---

### Post by Dennis N on 2022-03-27
> What is the version of Shotcut on Ubuntu repo?

Use apt to query the repository for the version of Ubuntu you are using:
```
apt show shotcut
```

---

### Post by satimis on 2022-03-27
> **Dennis N said:**
> Use apt to query the repository for the version of Ubuntu you are using:
```
apt show shotcut
```
Thanks for your advice.

$ apt show shotcut | grep Version```


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

Version: 20.02.17-2

```

The Shotcut version on repo is 20.02.17-2

I have download 2 Shotcut packages on Shotcut website;
1)
shotcut-linux-x86_64-220130.AppImage
2)
shotcut-linux-x86_64-220130.txz

I'll test the 2nd package on a Ubuntu 20.04 VM

To decompress 2) package, I'll run;```

$ xz -d < shotcut-linux-x86_64-220130.txz | tar xvf -

```
If wrong please advise me.  This is my 1st time to decompress .txz package

Besides can I install Shotcut direct on its tarball without further decompress it?

Thanks

Regards

---

### Post by Dennis N on 2022-03-27
```
If wrong please advise me. This is my 1st time to decompress .txz package

Besides can I install Shotcut direct on its tarball without further decompress it?

Thanks
```

1) Sorry, never used xz, and I don't generally use tar command. I would use Archive Manager which takes care of it all. 
2) You need to extract the Shotcut folder from the archive before running. The executable is inside the Shotcut.app folder which is inside the Shotcut folder.

---

### Post by satimis on 2022-03-28
Hi  Dennis,

I can't extract shotcut-linux-x86_64-220130.txz

xz -d < shotcut-linux-x86_64-220130.txz | tar xvf - ```

xz: (stdin): File format not recognized
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors

```

$ tar xf shotcut-linux-x86_64-220130.txz ```

xz: (stdin): File format not recognized
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```

$ tar xf shotcut-linux-x86_64-220130.txz --use-compress-program xz```

xz: (stdin): File format not recognized
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```

Archive Manager```

Extraction not performed
Close

```

Finally I run shotcut-linux-x86_64-220130.AppImage

Regards

---

### Post by Dennis N on 2022-03-28
> I can't extract shotcut-linux-x86_64-220130.txz
I used Archive Manager and it works. Try it instead of the terminal stuff.

---

### Post by satimis on 2022-03-29
Hi Dennis,

The previous shotcut-linux-x86_64-220130.txz package is broken.  I have re-download a new one on Shotcut website

Extract shotcut-linux-x86_64-220130.txz on Terminal running;
$ xz -d < shotcut-linux-x86_64-220130.txz | tar xvf -

Shotcut (folder)
Shotcut.app
Shotcut.decktop

Shotcut.app (folder)
bin
lib
share
ffmpeg
ffplay
ffprobe
shotcut
source-me
version

I suppose "shotcut" is the start-script
On File Manager, double-click "shotcut' without response.  I can't start it.

But on Terminal run;
$ ./shotcut  (script)

I can start Shotcut without problem.  I'm still trying to figure out the problem

---


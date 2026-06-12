---
title: "Xubuntu's &quot;Software&quot; does not run!"
date: 2017-01-01
forum: General Help
---

### Post by arashk on 2017-01-01
Hello,
When for the first time I clicked on a Xubuntu's application named "Software", it encountered an error and was unable to start.

What is wrong and what is the solution?

Have a happy time
Arashk

---

### Post by bearlake on 2017-01-01
If its a fresh install, I would try using "Software Updater" first and update your system.

There was a bug in "Software" which was fixed after taking the update.

---

### Post by arashk on 2017-01-01
> **bearlake said:**
> If its a fresh install, I would try using "Software Updater" first and update your system.

There was a bug in "Software" which was fixed after taking the update.

Yes, it is a fresh install. I will try "Software Updater". Thank you for the information.

[B]On "Software Updater" which update(s) is (are) related to resolving this bug? 
[/B][SIZE=1](Tell me if you need a screenshot of my "Software Updater".)[/SIZE]

---

### Post by bearlake on 2017-01-01
It was fixed sometime a go. Not sure which update fixed it.

I use Synaptic Package Manager myself or the command line.

```
sudo apt-get install synaptic

sudo apt-get install apt-xapian-index
```

---

### Post by arashk on 2017-01-01
> **bearlake said:**
> It was fixed sometime a go. Not sure which update fixed it.

I use Synaptic Package Manager myself or the command line.

```
sudo apt-get install synaptic

sudo apt-get apt-xapian-index
```

1. Before this latest post of yours, I used Software Updater to update "Software". It was updated successfully. I restarted. When I clicked on Software, the waiting sign began to turn but again Software did not start. 
2. I have Synaptic and send you a picture at the attachment. It says Software has the latest version and this shows that the update process has been successful.
3. What is apt-xapian-index for? I entered "sudo apt-get apt-xapian-index" in the Terminal and it replied that "E: Invalid operation apt-xapian-index".

---

### Post by howefield on 2017-01-01
> **arashk said:**
> 3. What is apt-xapian-index for?

In the context of Synaptic Package Manager, it enables a search field rather than the default search button.

It was removed from the default installation due to being buggy with performance issues although remains in the repositories if you want to manually install it.

PS. Your install command is missing "install" ie.. should be 

```
sudo apt-get install apt-xapian-index
```

---

### Post by Yellow Pasque on 2017-01-01
Run it from the terminal to get a specific error message. Otherwise, you're shooting in the dark.

---

### Post by arashk on 2017-01-01
> **Temüjin said:**
> Run it from the terminal to get a specific error message. Otherwise, you're shooting in the dark.

What should be typed in the terminal to run it?
I typed "gnome-software" and entered but Terminal did not returned anything.

---

### Post by howefield on 2017-01-01
Try...

```
ubuntu-software
```

---

### Post by arashk on 2017-01-02
> **howefield said:**
> Try...

```
ubuntu-software
```

"ubuntu-software" is different from "gnome-software". "ubuntu-software" is not installed on my xubuntu.

---

### Post by vasa1 on 2017-01-02
> **arashk said:**
> "ubuntu-software" is different from "gnome-software". "ubuntu-software" is not installed on my xubuntu.

They're the same but renamed so you have to use ubuntu-software from the terminal!

```
$ apt show ubuntu-software
Package: **ubuntu-software**
Version: 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1
Priority: optional
Section: gnome
Source: **gnome-software**
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 174 kB
Depends: gnome-software (= 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1)
Homepage: https://wiki.gnome.org/Apps/Software
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntukylin-desktop
Supported: 5y
Download-Size: 11.6 kB
APT-Sources: http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Description: Utility for browsing, installing, and removing software
```

---


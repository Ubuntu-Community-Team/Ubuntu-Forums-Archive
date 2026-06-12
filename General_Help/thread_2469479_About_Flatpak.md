---
title: "About Flatpak"
date: 2021-11-30
forum: General Help
---

### Post by satimis on 2021-11-30
Hi all,

Flatpak is a package management utility allowing to distribute, install and manage software without needing to worry about dependencies, runtime, or the Linux distribution.

Flatpak is available on repo.

Whether after having installed this package, in future on installing a new package on Ubuntu no need to worry about dependencies etc. ?

Regards

---

### Post by Dennis N on 2021-11-30
> **satimis said:**
> ...Flatpak is available on repo. Whether after having installed this package, in future on installing a new package on Ubuntu no need to worry about dependencies etc. ?
Regards
Flatpak applications in general depend on separate support packages (called runtimes) being installed as well. Different Flatpak applications don't all use the same runtimes, so you may have a number of these runtimes installed as well as the applications. But, you don't need to worry about them - they are automatically installed if needed.

---

### Post by satimis on 2021-11-30
> **Dennis N said:**
> Flatpak applications in general depend on separate support packages (called runtimes) being installed as well. Different Flatpak applications don't all use the same runtimes, so you may have a number of these runtimes installed as well as the applications. But, you don't need to worry about them - they are automatically installed if needed.
Thanks for your advice.

1)
Whether during installing a new package if the new package needs a new runtime, the new runtime will be pulled automatically?

2)
Do I need installing a runtime first on installing Flatpak.  If YES, I'll follow below document to install deno-runtime

How To Install Deno JavaScript Runtime on Ubuntu 20.04 LTS
[https://idroot.us/install-deno-javascript-runtime-ubuntu-20-04/](https://idroot.us/install-deno-javascript-runtime-ubuntu-20-04/)

unzip already installed on Ubuntu 20.04
$ which unzip
/usr/bin/unzip

Thanks

Regards

---

### Post by deadflowr on 2021-11-30
1)Yes
2)No

---

### Post by satimis on 2021-12-01
> **deadflowr said:**
> 1)Yes
2)No
Thanks

To 2) above, my understanding is only to install Flatpak ?

Regards

---


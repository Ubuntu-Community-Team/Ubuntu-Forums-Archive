---
title: "The following packages have been kept back (UPGRAD)"
date: 2007-05-22
forum: General Help
---

### Post by loathsome on 2007-05-22
Hi,

When I'm upgrading my Feisty from the terminal, I get this message ```
The following packages have been kept back:
  hal

```

Though, the Update Manager wants me to download this update. Why is it "kept back"?

---

### Post by mitch.c on 2007-05-22
> **loathsome said:**
> Hi,

When I'm upgrading my Feisty from the terminal, I get this message ```
The following packages have been kept back:
  hal

```

Though, the Update Manager wants me to download this update. Why is it "kept back"?

If you do an 'upgrade' packages that would cause installation or removal of other packages are kept back. If you do 'dist-upgrade' packages may be installed or removed to facilitate installation of a package. You might try:
```
$ sudo apt-get -s dist-upgrade
```
This will show you what packages will be installed/removed without actually taking action.

The other possibility is that the package has been manually marked hold.

---

### Post by loathsome on 2007-05-22
Great, thanks for your reply! :KS

---

### Post by boob11 on 2007-11-22
thnx    :popcorn:

---

### Post by Blofeld on 2007-11-27
Thanks.
But why is > apt-get upgrade holding back the packages that **Update Manager** is willing to install?
Different strategies?

---

### Post by Blofeld on 2007-11-27
Update Manager returns:
```
An error occurred
The following details are provided:
E: /var/cache/apt/archives/transmission-cli_0.91.dfsg-1~feisty1_i386.deb: trying to overwrite `/usr/bin/transmission-daemon', which is also in package transmission
E: /var/cache/apt/archives/transmission-gtk_0.91.dfsg-1~feisty1_i386.deb: trying to overwrite `/usr/share/pixmaps/transmission.png', which is also in package transmission
```
:confused:

---


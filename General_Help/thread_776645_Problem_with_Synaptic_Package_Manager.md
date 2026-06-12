---
title: "Problem with Synaptic Package Manager"
date: 2008-04-30
forum: General Help
---

### Post by TuPhat on 2008-04-30
Seeking some help here.  On 8.04, I am unable to install/uninstall any packages to due some broken packages.   I have 3 things in my Synaptic Package Manager that are broken, f-spot, libgnome2.0-cil, and p7zip-rar.  I can not reinstall or remove any of these packages due to an error.

The error message I receive is
dpkg: parse error, in file 'var/lib/dpkg/status' near line 20893:
invalid package name (character "'' not allowed (only letters, digits and characters '-+_'))
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

---

### Post by garyedwardjohnston on 2008-04-30
I'm installing right now and can't access synaptic for perfect instructions but you can filter the list by broken packages and fix them.

Also try switching the server to the main server in sources.

---

### Post by TuPhat on 2008-05-01
Thanks garyedwardjohnston.   I know how to filter down to the broken packages, I can see them but I can't fix them.  When I try to mark them for reinstallation, deletion or permanent delete, the package manager always comes up with the error message.   As of right now, I can not use package manager to get updates or fix my broken packages, in effect the package manager is broken for me.

I have tried updating my sources with other servers.   I have tried this many times and the problem still exists. 

Anyone else have any ideas before I reinstall.

---

### Post by Monicker on 2008-05-01
Try this from a terminal session, and post the output here:

```
sudo apt-get -f install
```

---

### Post by oldos2er on 2008-05-01
In Synaptic under the Edit menu, choose Fix Broken Packages.

---

### Post by TuPhat on 2008-05-03
> **Monicker said:**
> Try this from a terminal session, and post the output here:

```
sudo apt-get -f install
```

Here is the output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgnome-vfs2.0-cil p7zip-full
Suggested packages:
  monodoc-gtk2.0-manual
The following NEW packages will be installed:
  libgnome-vfs2.0-cil p7zip-full
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1270kB of archives.
After this operation, 3535kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by garyedwardjohnston on 2008-05-04
Did you try to switch to "Main Server" in sources?

---

### Post by stankopp on 2008-05-08
How do I go about changin my source to Main Server.

---

### Post by stankopp on 2008-05-08
Clicking on system/software sources does absolutely nothing.

---

### Post by stankopp on 2008-05-08
My problem has been solved.  It was actually an "unable to resolve host" issue.

---


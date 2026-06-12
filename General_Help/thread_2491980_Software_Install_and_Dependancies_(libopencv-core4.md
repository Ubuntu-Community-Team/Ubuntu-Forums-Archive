---
title: "Software Install and Dependancies (libopencv-core4.2)"
date: 2023-10-26
forum: General Help
---

### Post by akmartinez12 on 2023-10-26
Hello everyone,

I'm still relatively new to Linux.  I'm currently running Ubuntu 23.10.1.

I have a vision disability and I need to use a document reader from IPEVO.  They provide an application for Linux call IPEVO Visualizer v1.1.4.39.  It's kind of like a USB camera designed for reading text or print from books or other  documents.

I downloaded and tried to install the software:

```

sudo dpkg -i visualizer_1.1.4.39_all.deb 

```

... and I receive the following output:

```

Selecting previously unselected package visualizer.
(Reading database ... 221163 files and directories currently installed.)
Preparing to unpack visualizer_1.1.4.39_all.deb ...
Unpacking visualizer (1.1.4.39) ...
dpkg: dependency problems prevent configuration of visualizer:
 visualizer depends on libuvc0 (>= 0.0.6); however:
  Package libuvc0 is not installed.
 visualizer depends on ffmpeg (>= 3.4.4); however:
  Package ffmpeg is not installed.
 visualizer depends on libopencv-core4.2; however:
  Package libopencv-core4.2 is not installed.
 visualizer depends on openjdk-8-jre; however:
  Package openjdk-8-jre is not installed.


dpkg: error processing package visualizer (--install):
 dependency problems - leaving unconfigured
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for gnome-menus (3.36.0-1.1ubuntu1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 visualizer

```

I tried to manually install the dependancies:

```

sudo apt install libuvc0 ffmpeg libopencv-core4.2 openjdk-8-jre

```

... and I receive the following output:

```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package libopencv-core4.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'libopencv-core4.2' has no installation candidate

```

I do not know how to proceed or how to correct this issue.  I've been trying to search and found some information regarding libopencv-dev but am unsure if this is the route I should take for fear of corrupting the current install of Ubuntu.

Any help would be appreciated.

P.S.  I hope I formatted this post correctly.  Let me know.  I was informed from a few previous posts that I needed to block code and other things.  Still trying to navigate and follow protocols.  Thanks...

---

### Post by MAFoElffen on 2023-10-27
You said you are on 23.10.1 (Mantic).

For Mantic, the package would be 'libopencv-core406', which is version 4.6.0, which is a newer version than 4.2.0...

---

### Post by deadflowr on 2023-10-27
The download page tells you it only runs on Lunux Ubuntu 20.04.
[https://us.ipevo.com/pages/software]("https://us.ipevo.com/pages/software")
they'll need to update it if they are gong to support newer releases.

lunux, lol

---

### Post by akmartinez12 on 2023-10-27
Thank you to you both!

I tried installing the updated libopncv and then install visualizer but it did not work.  Visualizer still required the older version.

I will contact the vendor and let them know and ask when an updated version might be available.

Thanks again.

---


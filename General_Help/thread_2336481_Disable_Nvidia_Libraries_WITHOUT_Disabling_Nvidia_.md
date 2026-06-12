---
title: "Disable Nvidia Libraries WITHOUT Disabling Nvidia Driver"
date: 2016-09-08
forum: General Help
---

### Post by springshades on 2016-09-08
This is going to take some background explanation since it probably sounds stupid.

First, this is a server system which is having an issue that is probably very rare for a server but possibly more common for some laptops and desktops which is why I'm posting to general help. Second, I'm attempting to find a workaround for an issue caused by a variety of bugs in Ubuntu's X stack and the Nvidia driver packages (version 367).

I have on hand a group of HPC servers which are GPU accelerated using Nvidia GTX 1070 cards. In addition, I have access to quite a few HPC servers as well as a few storage servers which are NOT GPU accelerated.

Software setup: CUDA acceleration for the GTX 1070 cards requires nvidia drivers with a minimum version of 367 (we're using the graphics-drivers PPA) and CUDA toolkit version 8.0. We have this setup with some machines on Ubuntu 14.04 and some on Ubuntu 16.04. The GTX 1070 cards are ONLY for compute. The "primary" graphics card is an ASPEED brand which uses the "ast" drivers. Neither of these cards are actually used for anything graphical, as the servers boot to a command line without a GUI, but I set these up so that you plug a monitor into the ASPEED card rather than the nvidia cards.

Goal: X forwarding with 3D support to use something like pymol or VMD from a different machine to analyze and view experimental results. So in this case, there is a local machine (which is the X server) which has a graphical interface and a remote machine which is the CUDA accelerated server described above (which is the X client). The nvidia drivers CANNOT be uninstalled or disabled.

For testing I have AT LEAST one machine with each of the following: (1) Ubuntu 14.04 server w/ nvidia drivers, (2) Ubuntu 16.04 server w/ nvidia drivers, (3) Ubuntu 14.04 server w/o nvidia drivers, (4) Ubuntu 16.04 server w/o nvidia drivers, (5) CentOS 7 server w/o nvidia drivers, (6) Ubuntu 16.04 client/desktop w/ nvidia drivers, (7) Ubuntu 14.04 client/desktop w/o nvidia drivers, (8) Ubuntu 16.04 client/desktop w/o nvidia drivers, (9) CentOS 7 client/desktop w/o nvidia drivers.

Summary of problem and testing: (1) ALL desktops can successfully use 2D X forwarding with ALL servers. (2) ALL desktops can successfully use 3D X forwarding with servers that DO NOT have nvidia drivers installed. (3) The desktop with nvidia drivers can successfully use 3D X forwarding with the servers that have nvidia drivers installed after a bunch of hacky changes. (4) The desktops WITHOUT nvidia drivers CANNOT use 3D X forwarding with the servers that DO have nvidia drivers.

I believe the issue is with the servers using the nvidia libraries that replace the standard mesa libraries (e.g. libGL and libGLX), so I'd like to disable those libraries and have the server favor using the standard ones instead. However, I don't know of a way to force this other than the solution possibly having something to do with ldconfig. This would be easy if I could simply uninstall the nvidia drivers, but the *primary* purpose of the servers is CUDA accelerated compute. The *secondary* purpose of the servers would be analysis and viewing the data. If the only way to attempt to do this is some sort of nightmare hybrid setup (I'm not going to even try to run bumblebee on a production server) then we simply won't be able to do both of these things on one server.

---


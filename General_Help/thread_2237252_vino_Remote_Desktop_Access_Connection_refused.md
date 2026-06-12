---
title: "vino Remote Desktop Access Connection refused"
date: 2014-07-31
forum: General Help
---

### Post by daniel171 on 2014-07-31
Hi,

I've setup a remote desktop on Lubuntu 12.04 following these instructions exactly. The idea is to manage it as it is used for signage and won't have a keyboard and mouse attached.
[https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)

Under the Desktop Sharing Preferences window I checked "Allow other users to control your desktop" and un-checked all security options.

So far every connection attempt has been unsuccessful using either a TightVNC client on windows or UltraVNC running on Windows. The error it provides is Connection Refused: Connect. The same clients have no issues connecting to a 12.04 Ubuntu machine using the pre-installed desktop sharing service. All machines are on the same local network and I have no plans to make them accessible outside the network.

This is my first attempt at setting up Lubuntu Desktop sharing.  Any troubleshooting tips would be extremely helpful.

Thanks!

---

### Post by mörgæs on 2014-07-31
Lubuntu 12.04 is out of support. Before going further I recommend a fresh install of 14.04.1.

---

### Post by daniel171 on 2014-07-31
Unfortunately the [XIBO]("http://xibo.org.uk/manual/index.php?toc=getting_started&p=install/install_python_client") signage solution we are using is only supported on 12.04. It refused to install on a later version.

---


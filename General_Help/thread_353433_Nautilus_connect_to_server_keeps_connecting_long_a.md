---
title: "Nautilus connect to server keeps connecting long after disconnect"
date: 2007-02-04
forum: General Help
---

### Post by mikeyrb on 2007-02-04
I was having some internet issues earlier today relating to an ISP's router.  In the mean time, I was bored and was running Wireshark to see what my computer was up to.  I noticed it was trying to resolve dns entries for some servers I had connected to (SSH or webdav) using Nautilus' Connect to Server dialog.  I have not connected to some of these servers in over a month, if not more.  I noticed they have entries in the .nautilus directory of my home dir, as well as the metafiles directory under that.  Could one of these files be causing nautilus to connect to them?  I've had issues before where after I connect to an ssh server using this feature, and I shut down the remote server, then nautilus takes 100% cpu.  This can happen even if I think I've closed out/ejected the connected server.  Any ideas?

---


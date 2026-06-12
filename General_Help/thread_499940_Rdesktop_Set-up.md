---
title: "Rdesktop Set-up"
date: 2007-07-13
forum: General Help
---

### Post by strange_cathect on 2007-07-13
I am dual booting XP and Ubuntu.  I have one program that I simply have to use on my XP partition called Biblioscape.  I want to use Rdesktop to run this program within Ubuntu.

Is it possible to use rdesktop to access a windows program that exists on a different partition on the same hard drive?  Or does this need to exist on another machine alltogether?

If it is possible to do this, are there any good tutorials for a set up?

Thanks.

---

### Post by vanadium on 2007-07-13
In order to access the program using rdesktop, the program must be running elsewere. That can in fact be in a virtual machine on the same computer under Ubuntu. I do not have the experience myself, but that is the principle.

Before trying to set up a virtual machine, did you try installing and running the program with wine? If it runs, you will be able to navigate to the ntfs partition and open the necessary files there. However, you will probably also need write access on the ntfs partition for this to work fully. This will require you to install ntfs-config (and ntfs-3g). It is currently safe to use, and in fact will be included by default in the next Ubuntu release.

---


---
title: "Dolphin shows [Invalid protocol]"
date: 2016-11-12
forum: General Help
---

### Post by YeongMin on 2016-11-12
Ubuntu 16.04 LTS. Installed Dolphin via Synaptic. Installed good. Runs good. All the features are there; but when I try to connect to a Windows network share by typing:  [smb://server/] or [smb://server/shared-temp/] or [smb://192.168.1.250], it gives the error "Invalid protocol". When I click on the Network icon on the left in "Places", nothing happens. The entry location for Network is [remote:/].

Accessing Windows network shares in Nautilus works as intended.

Some help please.

For testing purposes, I uninstalled Dolphin and reinstalled using the Ubuntu Software center. Same results.

---

### Post by SeijiSensei on 2016-11-12
I'm a Kubuntu user and have never encountered this problem.

At first I thought it might be a missing dependency with libsmbclient being the most obvious candidate.  But running "dpkg -s dolphin" doesn't list that as a dependency.  There is [this thread]("https://bugs.documentfoundation.org/show_bug.cgi?id=67527") about problems with opening files from LibreOffice, but it's old and may be too LO-oriented. Also KDE uses its own method of accessing files with so-called "kio-slaves" which would be missing on a GNOME-based installation.  Perhaps the functionality of libsmbclient is incorporated in those.

As a test, see if you can access an smb:// URL from within Nautilus rather than Dolphin.  If that works, perhaps you should just use that instead of Dolphin for this purpose.  Also, if you can connect to a machine using SSH, see if the fish://server/share protocol works within Dolphin.  I use that all the time to connect to remote servers.  If that also doesn't work on a GNOME-flavored machine, then the problem may lay deep within the architectures of the two desktop environments.

If you need to connect to a particular machine routinely, you might consider mounting its share(s) directly into the filesystem with CIFS: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by YeongMin on 2016-11-12
I've used Kubuntu in the past with no issues as well. Yes, smb://server/ works in Nautilus. And yes, the SMB shares are Bookmarked in Nautilus and works as intended.

I would rather use Dolphin exclusively for several reasons, including split view, highlight to select, fully editable sidebar, to name a few.

Interesting find: I just installed PCManFM and it works as intended. This is my second choice, so I'll use that instead.

Issue not resolved; but a good workaround/alternative solution found.

Thanks, SeijiSensei for your input.

---


---
title: "he repository 'cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish"
date: 2023-03-31
forum: General Help
---

### Post by jgw on 2023-03-31
I am seeing:
```

E: The repository 'cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: https://apt.sonarr.tv/ubuntu/dists/focal/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.

```

I have searched for this in ppa's and can't find it.  I have read any number of suggestions but I should have this to start (I  think).  I would really like to get rid of it but have failed.

Thank you...........

---

### Post by ajgreeny on 2023-03-31
This has nothing to do with a ppa but is simply because the CD from which Ubuntu used to be installed, is still listed in your sources.

Open up **Software and updates** from your Activities or menu system depending on which DE version you're using and remove the selection tick from the box by the listed CD in the left hand pane, leaving the others still selected then try updating again.

---


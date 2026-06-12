---
title: "want to upgrade using CD [Resolved]"
date: 2007-02-13
forum: General Help
---

### Post by Entity` on 2007-02-13
I want to use the 6.06 Dapper CD to upgrade from Breezy.  How do I do that?

---

### Post by etank on 2007-02-13
I think that I saw in the past that putting a Edgy CD in a Dapper box that it noticed it automatically. Try placing the CD in to drive and see if it works on Breezy as well.

---

### Post by aysiu on 2007-02-13
You'll need the Dapper **Alternate CD** first of all. You cannot use the *Desktop CD* to upgrade.

Once you have the *Alternate CD*, type these commands into the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.breezy
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Entity` on 2007-02-17
can someone please provide a useable link to get the _*Alternate CD*_ as a ***.torrent*** file so I can use azureus to download it?

---

### Post by Maestro23 on 2007-02-17
> **Entity` said:**
> can someone please provide a useable link to get the _*Alternate CD*_ as a ***.torrent*** file so I can use azureus to download it?

Read the section for BitTorrent users: [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by Entity` on 2007-02-17
thanks yall

---


---
title: "2 Questions"
date: 2008-07-07
forum: General Help
---

### Post by adamant715 on 2008-07-07
Ok, 1st question is, where is the Gimp folder? I cant find it, and does anyone want to explain me to how you download programs and stuff? I find it pretty confusing:(

---

### Post by iaculallad on 2008-07-07
> **adamant715 said:**
> Ok, 1st question is, where is the Gimp folder? I cant find it, and does anyone want to explain me to how you download programs and stuff? I find it pretty confusing:(

Gimp Folder location:

```
cd ~/.gimp-x.x
```

x.x = represents the version number of Gimp installed in your Ubuntu machine.

**~** = You're Home Directory

Or you could use the locate terminal command to search for "gimp"

```
locate gimp
```

Downloading items is pretty much the same with windoze. Click on the link and automatically, the download windows pop-up giving you the option to open it with the default application or download it to your Desktop.

EDIT: You too could use wget (a non-interactive downloader) to download file/files from the Internet.

---

### Post by Phixion on 2008-07-07
You can also download stuff through the repositories.

System > Admin > Synaptic Package Manager

If you know the name of the application just do:

sudo apt-get install vlc (for example)

---

### Post by leito666 on 2008-07-07
You could also download software through Synaptic

---

### Post by adamant715 on 2008-07-08
> **iaculallad said:**
> Gimp Folder location:

```
cd ~/.gimp-x.x
```

x.x = represents the version number of Gimp installed in your Ubuntu machine.

**~** = You're Home Directory

Or you could use the locate terminal command to search for "gimp"

```
locate gimp
```

Downloading items is pretty much the same with windoze. Click on the link and automatically, the download windows pop-up giving you the option to open it with the default application or download it to your Desktop.

EDIT: You too could use wget (a non-interactive downloader) to download file/files from the Internet.The installer thing helped, but the Gimp thing did nothing..

---


---
title: "Can't Install any updates"
date: 2014-11-02
forum: General Help
---

### Post by dallase1 on 2014-11-02
I can no longer install any updates on my Ubuntu Release 12.04 (precise) 64-bit Kernel Linux 3.2.0-67-generic GNOME 3.4.2.

When ever I try to install updates or check for updates I get these error messages.


   Failed to load the package list 
  
 This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.
 

 E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
 

 

 Could not initialize the package information 
  
 An unresolvable problem occurred while initializing the package information. 
  
 Please report this bug against the 'update-manager' package and include the following error message: 
  
 'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'


I also can not install any new apps from the Ubuntu Software Center.

Why is this happening and how do I fix it?.

---

### Post by spacesamurai2 on 2014-11-02
Looks like you have a corrupted repo. I would recommend trying to remove it and updating again. Maybe something like:

```

sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner  _i18n_Translation-en
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Bucky Ball on 2014-11-02
You might want to look through [(https://duckduckgo.com/?q=Failed+to+load+the+package+list++12.04)"]HERE]("[https://duckduckgo.com/?q=Failed+to+load+the+package+list++12.04).

A tip: Please search before posting. ;)

First link on the link I gave. Fix is in post four but read the posts before and a couple after.

If this doesn't work, try [THIS]("A tip: Please search before posting. ;)"). Let us know which worked, if it did.

---


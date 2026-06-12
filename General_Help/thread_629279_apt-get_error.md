---
title: "apt-get error"
date: 2007-12-02
forum: General Help
---

### Post by ethosX on 2007-12-02
E: Problem parsing dependency Recommends
E: Error occurred while processing language-pack-gnome-tr-base (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_dists_gutsy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

apt-get install "anything" gives me this error
apt-get update gives me this error

---

### Post by PmDematagoda on 2007-12-02
Try deleting the file that is mentioned:-
```

/var/lib/apt/lists/mx.archive.ubuntu.com_ubuntu_di sts_gutsy_main_binary-i386_Packages
```

Using:-

```
sudo rm /var/lib/apt/lists/"mx.archive.ubuntu.com_ubuntu_di sts_gutsy_main_binary-i386_Packages"
```

After deleting that file, do:-

```
sudo apt-get update
```

---


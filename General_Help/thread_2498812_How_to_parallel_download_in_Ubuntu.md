---
title: "How to parallel download in Ubuntu?"
date: 2024-06-28
forum: General Help
---

### Post by commodoreregion on 2024-06-28
Hello folks I am a user who is coming over from Arch Linux. pacman has parallel downloads builtin, which can be activated by editing the "ParallelDownloads" line in /etc/pacman.conf. Does apt have a similar feature right out of the box? If not, is there a script/hack that enables parallel downloading?

---

### Post by ActionParsnip on 2024-06-28
you could try apt-fast, may help. I'm not sure about parallel downloads but it pulls from multiple sources which makes the downloads of packages faster

---

### Post by ActionParsnip on 2024-06-28
OK according to:
[https://askubuntu.com/questions/1178237/download-multiple-packages-in-parallel-from-a-single-repository-with-apt](https://askubuntu.com/questions/1178237/download-multiple-packages-in-parallel-from-a-single-repository-with-apt)
it does do parallel downloads

---


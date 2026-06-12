---
title: "Where does the Archive Manager send files"
date: 2019-02-09
forum: General Help
---

### Post by jacatone on 2019-02-09
I'm using Ubuntu 18.04. Whenever I try unzipping a tar.gz file the Archive Manager sends the file somewhere but doesn't say where or allow you to select it. Why is this? Anyone know where or how to find them. Catfish doesn't always find it. Really stupid.

---

### Post by Impavidus on 2019-02-10
Which archive manager? I never really use any, but I just checked both file-roller and engrampa on my Xubuntu 18.10 and both offer you to select a directory for unpacking, defaulting to the directory where the archive is located and ignoring the current working directory from where the archive manager was started. Both also offer to view the files after unpacking, which should open the file manager (whichever you use) at the directory where the archive was unpacked. If you download an archive and don't want to store it, but directly open it in your archive manager, I think it would normally be stored in /tmp. Things stored in /tmp will be automatically removed on the next reboot. But it may depend on your settings and I think my settings aren't exactly default.

---


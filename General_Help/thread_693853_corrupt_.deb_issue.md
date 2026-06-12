---
title: "corrupt .deb issue"
date: 2008-02-11
forum: General Help
---

### Post by mshumer on 2008-02-11
Hello, hope you guys (and gals) can help.
I installed a writing software called writer's cafe (writerscafe.co.uk) and was having problems so I tried to reinstall. Problem was their server had corrupted the .deb file. Now when I have files to update, I get the following alert:

"E:/var/cache/apt/archives/firefox-gnome-support_1.5.dfsg+1.5.0.15~prepatch080202a
-0ubuntu1_i386.deb:files list file for package 'writerscafe' contains empty filename

I managed to fix the program writerscafe by reinstalling but I still have this error which won't allow any updates to other software. Where do I find the files list for the package 'writerscafe'?

Thanks in advance for all your help.

---

### Post by drs305 on 2008-02-11
You can start by running  (small L)
```
sudo find / | grep writerscafe
```
to see where the majority of the files are located. If you get too much information on the screen at one time, add " | less " at the end of above.

Synaptic has an option that might help as well under Edit, Fix Broken Packages if the package is listed there.

Additionally, anything in the var/cache/apt/archives can be safely removed.

---


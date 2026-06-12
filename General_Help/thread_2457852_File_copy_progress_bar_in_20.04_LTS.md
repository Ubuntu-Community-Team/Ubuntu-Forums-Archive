---
title: "File copy progress bar in 20.04 LTS?"
date: 2021-02-10
forum: General Help
---

### Post by John Nagle on 2021-02-10
Is there some way to get a file progress bar in Ubuntu 20.04 LTS? I've read

[https://sourcedigit.com/21466-ubuntu-show-copy-dialog-not-working-ubuntu-nautilus-file-progress-bar/](https://sourcedigit.com/21466-ubuntu-show-copy-dialog-not-working-ubuntu-nautilus-file-progress-bar/)

but it doesn't work.

---

### Post by deadflowr on 2021-02-10
There is no bar.
There is a circle that will appear in the top right area of the file manager when active.
The circle will slowly fill in as the copy/move takes place until it's full, and then it will disappear.
Click on the circle at any time to get the overall details and options.

It can be sporadic, and some file transfers won't even show it.
Small files might transfer too fast for it to even initiate the progress indicator.
Some issues with it in general can be found in this bug report:[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1726516]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1726516")

---

### Post by TheFu on 2021-02-10
Maybe just use a different file manager program?
Nautlus, Thunar, Caja, Nemo, pcmanfm are some examples. There must be 20 others.
[https://en.wikipedia.org/wiki/Comparison_of_file_managers#Cross-platform_file_managers](https://en.wikipedia.org/wiki/Comparison_of_file_managers#Cross-platform_file_managers)

---


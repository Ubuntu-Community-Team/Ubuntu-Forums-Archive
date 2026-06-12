---
title: "Problem Setting up New Computer"
date: 2023-03-24
forum: General Help
---

### Post by BarryM on 2023-03-24
I am trying to set up a new computer, and have a problem copying all my apps over. I did this successfully some time ago (2014) using the following commands:

From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade 

The --get-selections worked happily on my old computer, but
on the new computer
After the --set-selections i got a lot of error messages
the -y update seemed to work
the dselect-upgrade returned an error message Invalid operation dselect-upgrade

I suspect that there is a newer command sequence, but I can't figure out what to do, can anyone help? I am using 22.04.

---

### Post by TheFu on 2023-03-24
Packages are dropped.  You'll want to manually remove those from the list.
I moved to a newer LTS a few months ago and ran into a few issues.  I don't remember how I solved it, but I vaguely remember removing all lib* packages from the list and just feeding the list (created by **apt-mark showmanual**) into **apt install $(cat path/to/file-with-list)**

---


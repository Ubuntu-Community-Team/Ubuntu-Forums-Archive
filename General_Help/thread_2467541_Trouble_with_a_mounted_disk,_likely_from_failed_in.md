---
title: "Trouble with a mounted disk, likely from failed install of Kubuntu"
date: 2021-09-30
forum: General Help
---

### Post by pyryturunen1 on 2021-09-30
Hello, I have just recently installed Kubuntu and I had some problems during installation. One proposed solution was to install to my 2nd drive instead, which I did and the installation failed again. Later I successfully installed to the 1st drive. Now I'm having problems where there seems to be traces of that failed installation still on the drive. There's 2 issues I've noticed.

1. The directory name where the drive is mounted is a '7b6e448d-50de-45bb-8062-7edbe5d61524' and I can't rename it. Trying to rename it with the mv command I get 'Device or resource busy' including when I've just un- and remounted it just prior.

2. When booting the PC I'm put into the boot select menu where I have the following options
    Kubuntu    (this one is the correct one, ver. 21.20 on the 1st drive, nvme0)
    Advanced options for Kubuntu
    Kubuntu 21.04 on /dev/nvme1n1p2    (the bad installation on the 2nd drive, nvme1)
    Advanced options...

I've repartitioned the drive, but can't seem to get rid of the second partition. In my /dev directory I do not have a file named nvme1n1p2 and I don't see that partition on any partitioning tool.

---

### Post by bijayalaxmi1808 on 2021-09-30
Not sure if GParted will help here to get your job done of renaming the drive (or partition) you want to, but anyway you can give it a try.

Usually reformatting the whole drive should have replaced a new filesystem data and your second drive should come back to original state. Please check if you have done that correctly after that bad installation.

---


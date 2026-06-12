---
title: "View installed packages' sizes"
date: 2007-10-22
forum: General Help
---

### Post by Fibonacci on 2007-10-22
Hello,

After upgrating to Gutsy I noticed that circa 3GiB of previously free disk space were now in use, so I would like to remove some of the largest installed packages. Is there a way to view their sizes, not individually but all of the installed packages at once?

Thanks in advance,

-Fibo

---

### Post by ajgreeny on 2007-10-22
> Is there a way to view their sizes, not individually but all of the installed packages at once?Do you mean the size of the xxx.deb files which are downloaded when you apt-get or use synaptic, or do you mean the overall size of disk space used by the programs once installed?

For the first look in **/var/cache/apt/archives** where all the .deb files are cached.
For the second the easiest way is to use synaptic.  Go to **Preferences** and in the main tab click in the **"Show package properties in the main window"**.  Then in the "**Columns and font"** tab select to show **"Installed size"**.  Now using the Status filter in the right side bar you can check all installed package sizes.

If none of this helps and you want to see where your 3GB+ has gone to, get **filelight** from the repos and it will show your space usage graphically.

---

### Post by yjsword on 2007-10-22
sudo apt-get clean
:)

---

### Post by Fibonacci on 2007-10-24
> **ajgreeny said:**
> Do you mean the size of the xxx.deb files which are downloaded when you apt-get or use synaptic, or do you mean the overall size of disk space used by the programs once installed?

The second.

> **ajgreeny said:**
> For the second the easiest way is to use synaptic.  Go to **Preferences** and in the main tab click in the **"Show package properties in the main window"**.  Then in the "**Columns and font"** tab select to show **"Installed size"**.  Now using the Status filter in the right side bar you can check all installed package sizes.

Thank you. I'm currently removing large unused packages.

> **ajgreeny said:**
> If none of this helps and you want to see where your 3GB+ has gone to, get **filelight** from the repos and it will show your space usage graphically.

Is it something like a graphical frontend to du?

> **yjsword said:**
> sudo apt-get clean
:)

Only freed about 1.5 of the 3GiB, but thank you too.

---


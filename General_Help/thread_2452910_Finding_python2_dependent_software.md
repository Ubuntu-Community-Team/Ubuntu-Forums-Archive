---
title: "Finding python2 dependent software"
date: 2020-10-30
forum: General Help
---

### Post by benyjr on 2020-10-30
Now that we are 10 months into python2 being eol, I'd like to track down which applications are dependent on python2 so I can finally begin migrating off of python2 and have only python3 in use on my system.

What apt command would I use to find packages that require python2 to be installed?

Thank you.

---

### Post by dino99 on 2020-10-30
What i'm using : synaptic
select 'python2' (or yours) then check Dependencies -> dependants

or via python commands [https://stackoverflow.com/questions/12939975/how-to-list-all-installed-packages-and-their-versions-in-python](https://stackoverflow.com/questions/12939975/how-to-list-all-installed-packages-and-their-versions-in-python)

---

### Post by oldfred on 2020-10-30
I do not have python2 anymore and if I see some app wanting it, I do not install it.
depends & reverse depends
apt-cache showpkg python2.7

Not sure if Ubuntu 20.04 offers any apps with 2.7?

I have script to install my most favorite apps in groups. When a group showed it wanted python2, I did not install it and went back and installed each app to find the one that wanted python2. Updated script to exclude it.

One of my apps is calibre, author said he was not going to update.
[https://www.reddit.com/r/linux/comments/9wodtq/calibre_wont_migrate_to_python_3_author_says_i_am/](https://www.reddit.com/r/linux/comments/9wodtq/calibre_wont_migrate_to_python_3_author_says_i_am/)
But I now see it has a new python3 version calibre 5, so I can go back and install it. Snaptic shows 4.99, but python3 as depends.
[https://calibre-ebook.com/new-in/fourteen](https://calibre-ebook.com/new-in/fourteen)

You can also check by running the uninstall command without actually running it, just to see what it wants to uninstall. 
With older system where python2 is used for system, it offers to uninstall just about your entire system, or huge list.
Do not accept or say yes, but just use to check what it shows.
sudo apt remove python2.7
or sudo apt purge python2.7

---

### Post by mikewhatever on 2020-10-30
You can simulate an uninstall of python2 like this:

```
sudo apt-get -s remove python2.7
```

It should show which packages will have been uninstalled, but won't do anything else.

---


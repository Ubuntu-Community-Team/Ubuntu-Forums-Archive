---
title: "Making a Patched CD"
date: 2007-02-08
forum: General Help
---

### Post by Magiczero on 2007-02-08
Hey

Is there a way I can make a cd with all the patches on it so if I reinstall ubuntu I can just put in this cd and install the updates from it?

---

### Post by DagMan on 2007-02-08
I'm not sure what exactly you mean, but if you're wanting to reinstall and have a simple way to then apply all of the updates, and if you still have all of the updates on your computer, that is that if synaptic isn't automatically deleting them after install or after x many days have passed, then you can copy them along with most of everything else you installed, to a cd, then after reinstalling you can copy them back to the appropriate location and you wouldn't have to download everything all over again.

This would work with anything you've installed if your package manager isn't auto deleting things and I'm not sure how much of what Automatix does would need to be re-dowloaded (assuming you ran it and will re-run it) but I have a feeling it might need re-download.

It's still much easier to copy what packages you do have to a cd or some other external storage than to redownload everything.  If you have very little in your package manager storage then it would not be a huge help but it would be that much less to download... assuming that's the concern.


You'de want to get all the files ending in .deb located in /var/cache/apt/archives
What you don't want from that folder is a folder called partial and a file called lock.  Once you have them on Cd, you'de copy them back to that same directory after reinstalling.

I'd do it in this order for the reinstall.
-copy things back to /var/cache/apt/archives
-apt-get update or reload in synaptic
-get the updates, hopefully they were all saved and are on your hard drive
-Run automatix
-edit your sources.list file and update again
-install the rest of what you want to

If that isn't at all what you were looking for, it would be a good idea to say so, that way someone else can answer properly and not pass the thread by.

---

### Post by Magiczero on 2007-02-08
Basiclly I am looking for a way to get all the updates onto one cd so that I can have an up-to-date computer without downloading 533MB of updates when I reinstall!  So, I want to make a cd with updates on it so I can just put in the cd and install the updates as soon as I do a fresh install!

Also, Is there a ghosting software where I can make an image of my hard drive & boot from it?

---


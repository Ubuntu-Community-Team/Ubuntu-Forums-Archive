---
title: "Software demands outdated dependencies - MIMIO STUDIO 11.53"
date: 2019-10-28
forum: General Help
---

### Post by sduverge on 2019-10-28
I think this is where it belongs, if not, sorry in advance. I haven't posted in a long, long time.

So I am having the hardest time to install a software necessary to use a device at work, called **Mimio Teach**, it turns a regular magnetic board into a smart board.

Thing is the vendor's web page has a software available for Linux, version 11.53, problem is that it was meant for Xenial 16.04 so it's seriously outdated and won't accept newer replacement of certain dependencies to be installed.

Currently is demanding **libcurl3** which doesn't exist anymore, I can find **libcurl3_7.47.0-1**, that demanded **libssl1.00**. Installed Libssl1.0.0 and **libcurl3_7.47.0-1,** but it is still asking for **libcurl3**, I can't find libcurl3 alone anywhere. Where do I go from here?

About installing the windows version via playonlinux or wine, it requires netframeworks 4.6 and takes forever and took about 4gb of my HDD, don't know why, I have a chromebook 16GB SSD and 64GB microSD running Lubuntu to save space, but transferring wine an playonlinux to the SD card was a total nightmare and didn't work as it continued creating the virtual drives on the /home folder.

Please Help!

---

### Post by cruzer001 on 2019-10-29
I don't see a choice in this.  You must run 16.04.  Trying to install old dependencies will lead you to a never ending process of replacement that will most likely destroy your current system.
Sorry

---

### Post by kevdog on 2019-10-29
Honestly I'd install 16.04 within a VM and run your program there.

---


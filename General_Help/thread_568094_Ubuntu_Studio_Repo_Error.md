---
title: "Ubuntu Studio Repo Error?"
date: 2007-10-05
forum: General Help
---

### Post by Banjogator on 2007-10-05
Hello  Ubuntu Studio Support,
I am a musician and am really interested in installing Ubuntu Studio. 

I pasted the Studio script from your website [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

using the posted commands:

**Ubuntu Studio Repo**

Here's how to get access to our repo.

From a terminal run these 2 commands:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update


I received the following errors from the update manager. I'm running on an AMD 64 Bit machine:

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2)
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2)
[http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release:](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release:) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

Can I fix this script somehow or should I just wait for the Gusty AMD 64 release to come out some day?

Thanks much for your help!

Karl - BanjoGator

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

---

### Post by luctor on 2007-10-14
just found out (on #ubuntustudio) that the packages are in the regular ubuntu repos, no need to add a repo to the sources.list

---

### Post by Jussi01 on 2007-10-15
> **luctor said:**
> just found out (on #ubuntustudio) that the packages are in the regular ubuntu repos, no need to add a repo to the sources.list

This is correct for gutsy. (it was I who told you) (: However there are no 64 bit repos for feisty. At all. So you need to wait for gutsy.

HTH

Jussi

---


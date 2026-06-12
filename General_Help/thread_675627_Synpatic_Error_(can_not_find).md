---
title: "Synpatic Error (can not find)"
date: 2008-01-22
forum: General Help
---

### Post by Andrew07 on 2008-01-22
I went to install the build-essential package (for obvious reasons), but ran into some problems. First, it asked me to put my liveCD into the /cdrom/ drive. Never have it do that before, but I figured it had to get something off the CD and stuck it in.

Shortly after it pops up an error that says "could not be retrieved from server." The 3 files in questions are:

dkpg-dev
patch
build-essential (I'm assuming this one is failing because of the other two)

The IRC channel suggested trying a mirror, which I did, to the same result.

---

### Post by dcstar on 2008-01-23
> **Andrew07 said:**
> I went to install the build-essential package (for obvious reasons), but ran into some problems. First, it asked me to put my liveCD into the /cdrom/ drive. Never have it do that before, but I figured it had to get something off the CD and stuck it in.

Shortly after it pops up an error that says "could not be retrieved from server." The 3 files in questions are:

dkpg-dev
patch
build-essential (I'm assuming this one is failing because of the other two)

The IRC channel suggested trying a mirror, which I did, to the same result.

Did you you a "Reload" after you changed the settings to use the mirror?

---

### Post by ctswhole on 2008-01-23
What does your repository list consist of?  And you can stop Ubuntu from asking for your CD on an install if you either comment it out of your /etc/apt/sources.list or just open up Synaptic Package Manager and go to Settings ->Repositories and uncheck the CD/DVD option.

---

### Post by Andrew07 on 2008-01-23
> **ctswhole said:**
> What does your repository list consist of?  And you can stop Ubuntu from asking for your CD on an install if you either comment it out of your /etc/apt/sources.list or just open up Synaptic Package Manager and go to Settings ->Repositories and uncheck the CD/DVD option.

Commenting out the CD seems to have worked.

---


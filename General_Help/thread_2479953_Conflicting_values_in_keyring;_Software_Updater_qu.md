---
title: "Conflicting values in keyring; Software Updater quit working"
date: 2022-10-14
forum: General Help
---

### Post by mikethechap on 2022-10-14
I am trying to install the R statistical language. It appears I managed to do something with the keyrings that prevents me from even opening the software or software or software updater. 

Here's the error message in the terminal when I run ```
sudo apt update
```

```
sudo apt update
[sudo] password for study: 
E: Conflicting values set for option Signed-By regarding source https://cloud.r-project.org/bin/linux/ubuntu/ jammy-cran40/: /usr/share/keyrings/cran.gpg != /usr/share/keyrings/r-project.gpg
E: The list of sources could not be read.

```

I thought perhaps I could edit my keyrings from the terminal and that was perhaps the problem. I went to the /usr/share/keyrings folder and ran:
```
/usr/share/keyrings$ sudo apt update
E: Conflicting values set for option Signed-By regarding source https://cloud.r-project.org/bin/linux/ubuntu/ jammy-cran40/: /usr/share/keyrings/cran.gpg != /usr/share/keyrings/r-project.gpg
E: The list of sources could not be read.
```

Based on looking around, I tried to edit my sources:
```
/usr/share/keyrings$ ls
brave-browser-archive-keyring.gpg      ubuntu-advantage-ros.gpg
ubuntu-advantage-cc-eal.gpg            ubuntu-archive-keyring.gpg
ubuntu-advantage-cis.gpg               ubuntu-archive-removed-keys.gpg
ubuntu-advantage-esm-apps.gpg          ubuntu-cloudimage-keyring.gpg
ubuntu-advantage-esm-infra-trusty.gpg  ubuntu-cloudimage-removed-keys.gpg
ubuntu-advantage-fips.gpg              ubuntu-master-keyring.gpg
ubuntu-advantage-realtime-kernel.gpg
```

I looked for other solutions. I know (at least somewhat) how to remove sources in the Software app. 

I think I could work through this if I could just get the software application to open but neither Software nor Software Updater is opening. 

Thanks!

Mike Davis

---

### Post by MAFoElffen on 2022-10-14
Please run the [UbuntuForums 'syste-info']("https://github.com/UbuntuForums/system-info") script... 

In it are sections for sources.list and sources.d, where we might be able to match the source that is causing that error. I'm thinking it is a CRAN Mirror line. I don't (yet) see a key that would conflict with what is there, but... (LOL) We'll see.

But in the installation instructions on adding the repo line to the sources, you first add the key to the repo:
```

wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc

```
Which you could check if it is there via
```

ls /etc/apt/trusted.gpg.d/*

```
Then the sources line we are looking for should be from this line of the install instructions:
```

sudo add-apt-repository "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/"

```

---

### Post by mikethechap on 2022-10-14
:popcorn:

Thank you for pointing me in a great direction!

The system-info script was very valuable. I ended up deleting my custom repositories using the following:
```
sudo rm /etc/apt/sources.list.d/*
sudo apt update
```

That got things going again. I'll be more careful in which custom repositories I install in the future. 

Thank you for your time and assistance. If I can, I'll return the favor. 

Mike

---

### Post by MAFoElffen on 2022-10-15
Happy that all is going now.

Please use the "Thread Tools" link in the upper right of the page to mark this thread as Solved so that others can find your solution to help with their similar problems..

---


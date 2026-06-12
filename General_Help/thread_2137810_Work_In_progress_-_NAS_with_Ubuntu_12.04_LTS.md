---
title: "Work In progress - NAS with Ubuntu 12.04 LTS"
date: 2013-04-22
forum: General Help
---

### Post by Robert98374 on 2013-04-22
Good Afternoon!

As the title states i am running an old Dell Optiplex 745 with Ubuntu 12.04Lts, running without a hitch as of right now but fixing/adding features.

Goals

1. Running Headless - Able to connect through main windows 7 machine with TightVNC - Done
2. Able to share HD on ubuntu with the rest of network on SAMBA - Done
3. Run Plex and have pointed to media folders - Done but had to create folders directly on the file system so plex would see them (If i can be more efficient i would like some pointers)
4. Automatically run SABnzbd and set downloaded folders - Done
5. Automatically run Sickbeard and have folders pre-defined on where the shows are downloaded
6. Automatically run couch potato to watch for specific movies to download and have them downloaded to specific folder for movies
7. Work in progress auto start deluge, have it watch dropbox folder for torrent files from all the above or from other machines on network
    a. Issue with not being able to start the same instance of Deluge that has all the torrents already stored etc. 
    b. Issue with deluge not saving files to where was selected in UI and with command line
    c. Only able to create 3 labels atm through the gui
8. Have NAS automatically connect to VPN service


Unfinished Goals
1. Able to access files downloaded over the internet
    a. Wondering if dynamic DNS would be best or setup an FTP file server
2. Eventually upgrade system to a fully fledged build specific to a computer to be an NAS
3. Venture into creating a raid system (My Understanding the best would be raid 10)
4. Working with Handbrake & dropfolders so the google tv can play everything without compatibility issues
5. Wondering about efficiency of different desktop environment besides cinnamon but similar enough to unity that i can still use the guides already set up
6. Wanting to be able to control computer from phone so if temps spike or server needs to be reset i don't have to be home to do it
7. Eventually have a front end to replace the google tv so not so techy family can navigate


Thats it for now for my machine, i know some items can be considered novice but at the same time tweaking everything to work correctly and in sync has taken many hours of tweaking .conf files etc. If anyone has any suggestions/Comments/random outbursts just hollar and ill point ya in the right direction. My biggest concerns are the ones with deluge and doing some final tweaks with getting access through the internet

---

### Post by mastablasta on 2013-04-22
have you had a look at:

webmin
zentyal

openmediavault


not sure why you have desktop environment on headless mashcine.... but oh well...

---

### Post by Robert98374 on 2013-04-22
I also have webmin installed and running great but i noticed with it theres options for modules. Looked at the website and i cant find where to get them. As for the desktop environment, i don't feel comfortable completely going command line but eventually ill go that way

---

### Post by Robert98374 on 2013-04-22
With those other distros i would have to start from scratch, not really looking at going that way but thanks for the tip

---

### Post by mastablasta on 2013-04-23
> **Robert98374 said:**
> With those other distros i would have to start from scratch, not really looking at going that way but thanks for the tip

i think Zentyal is like webmin. a gui interface for server. it is also a separate distro.

edit: webmin modules: [http://www.webmin.com/standard.html](http://www.webmin.com/standard.html)

---

### Post by Robert98374 on 2013-04-24
Hmm...didnt find anything for Zentyal, but thanks for the heads up on the modules

---

### Post by Robert98374 on 2013-05-05
I'm noticing when the NAS is plugged in, it sucks major amounts of bandwidth and i was wondering if there was a tool that i could use to figure out what exactly is using so much?

---


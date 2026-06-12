---
title: "kubuntu hardy kde-4 resolution problems"
date: 2008-05-04
forum: General Help
---

### Post by rabbitnightmare on 2008-05-04
Ok I have been away from linux for a small while how can I get to where I can configure so I can get a higher resolution than 800x600...

---

### Post by NightwishFan on 2008-05-04
You can under system settings -> display. Make sure you check use settings on startup. If you only get 800x600 as max try to install the restricted drivers (if any) for your card. (Applications -> System -> Hardware drivers manager)

May the force be with you.

---

### Post by rabbitnightmare on 2008-05-04
well it lists my nvidia driver i allow it and it knocks it down to 640x400 am pulling my hair out lol

---

### Post by NightwishFan on 2008-05-04
With the driver enabled, reboot, and try:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the best you can, and if you are unsure use the default. After that again of course reboot, although just restarting the xserver might be good enough.

---

### Post by rabbitnightmare on 2008-05-04
awesome will try u know u never get this kinda service from windows this may keep me using ubuntu if this doesn't work am switching to either kde3 or gnome the latter is my favorite just wanted to give kde4 a spin

---

### Post by NightwishFan on 2008-05-04
Kde4 is far from full featured at the moment, I currently use it as I love the new concepts of the desktop and I like getting surprise new features with updates, I like to live on the bleeding edge. Kde3.5 (standard kubuntu) is a great release though.

Edit: Not saying Gnome isn't, but I do not like Gnome anymore.

---

### Post by rabbitnightmare on 2008-05-04
You know what I just realized a lot is missing like control center. I know KDE 3.5 like the back of my hand and I really do not like it. I am really loving what I am seeing in KDE4 though. I used to be a gear-head and I hope 4 re-invigorates me. I am not used to the *buntu's as I usually use another distribution. I just downloaded this version so I did not mess up my other config with KDE4. It was already pre-configured so I did not have to mess around with dependencies. It is truely sexy and I hope it keeps down this path of simplicity and beauty rather than the mess KDE3.5 is. Gnome has my heart for now and I am running away with my tail between my legs for now. I may actually try Ubuntu. I do not like the sudo this and sudo that though. Thank you for all of your help! You are awesome!:guitar:

---

### Post by NightwishFan on 2008-05-04
No problem. My advice is to stay with kde but, Gnome is great as well, especially Ubuntu.

Features coming in kde4:

Ports to Windows and Mac.

Phonon backend to utilize quicktime, directx, xine, etc when on supported platforms with a simple stack. For example if Xine will not work and you have another backend like gstreamer, it will try that next with no or very little visible lag. Most of the api for kde4 will work this way. (one bluetooth protocal will not work so it will instantly use the next one with little delay, also planned for wireless etc)

Solid device integration framework. An example policy might deal with your computer hibernating. You'd want network interfaces to go down and for network-enabled applications to gracefully handle the disconnection; USB devices should be synced to avoid data loss; CPU-intensive eye candy should be disabled to save battery power. If all KDE applications integrate Solid then this would become a reality.

A new desktop environment called Plasma, with many rewrites, also new menus coming. (Different from current 2, kmenu and kickoff). Also I love how everything is svg and scalable.

Decible, a new communication framework much like Solid and Phonon. Decibel aims to integrate all communication protocols into the desktop. As of now they have all their contacts in different applications: AOL, MSN, E-mail, Skype, etc. Decibel wants to put all contacts in one place and make it easier for the user to manage and communicate with his/her contacts.

There is more about it on the wikipedia page, frankly it all seems great, and they have a realistic chance of having it all work, and much of it may be ready by kde4.1 in a few months. As of now I am an early adopter but it is already very stable.

---


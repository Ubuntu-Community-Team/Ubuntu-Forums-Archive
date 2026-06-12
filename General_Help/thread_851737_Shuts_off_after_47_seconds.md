---
title: "Shuts off after 47 seconds"
date: 2008-07-07
forum: General Help
---

### Post by Falcon_14 on 2008-07-07
I am having a really strange problem with a fresh install of 8.04 on a Toshiba Satellite M35X-S309 laptop.  It has been running Win XP SP2 for years with no problems. I had been wanting to try out Ubuntu on this laptop for a while, and tonight I finally got around to installing Ubuntu, which I did from the 8.04.1 disk. 

It installs normally, and I boot it up the first time. everything seems normal, except for the text for my username and password is way too big - one dot in the password entry box takes up the entire width of the box.

Once I logged in everything seemed fine, so I looked away for a few seconds, and that is when I heard the hard drive spinning down. I looked back and the laptop was completely shut down. It was exactly as if I had held down the power button for a few seconds to force it to shut off.

I tried to restart it a few more times, and no matter what I did it would shut off without warning. I eventually started timing how long it would take it to shut off, and it seems to do so 47 seconds after the cursor appears for the first time. It also seems to be that I get an extra 10 seconds before it shuts off if I plug in the power adapter. 

I have felt the airflow coming out of the exhaust, and it does not seem to be any warmer than it was under XP and neither does the laptop itself.

---

### Post by un_dave on 2008-07-10
If you have a chance before it powers down, you should check the logs, and see if there's something in there. 

It may give you some insight into why it's shutting down. 

Also, does it shutdown if you boot to the live cd?

---

### Post by alex33 on 2008-07-25
I have exactly the same laptop and I had exactly the same problem. I tried to uninstall and install it again but now is even worse. The monitor shuts off before it installs ubuntu. I think the problem lies with the motherboard but I am novice on this stuff and I do not know exactly what to do.

If you do not want to install inside windows like me just install a previous edition and update later.

---

### Post by phidia on 2008-07-25
Maybe alex33 & falcon_14 want to compare/post their outputs of lshw?

---

### Post by iSKUNK! on 2009-11-12
See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400") for a likely solution. (In a nutshell: upgrade the laptop's BIOS)

---


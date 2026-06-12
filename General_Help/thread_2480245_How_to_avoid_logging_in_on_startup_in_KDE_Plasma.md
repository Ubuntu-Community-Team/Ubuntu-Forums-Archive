---
title: "How to avoid logging in on startup in KDE Plasma"
date: 2022-10-23
forum: General Help
---

### Post by Nosphky on 2022-10-23
I've reinstalled 22.04.1 UbuntuStudio with KDE Plasma three times now after having display glitches. (I've now removed the nvidia graphics card and at present, all seems ok).  I now have to login with my admin password every time I boot up. If I recall correctly, I didn't have to do that on the first installation of 22.04 KDE Plasma.

I've been using UbuntuStudio LTS versions since 14.04 (with Xfce) and never had to provide my password at initial boot up which always proceeded to completion with my user name fully logged in to my account.  I only needed my user password when carrying out some 'sudo' task.

I believe I did tick a box during the installation to bootup without login and I'd like, if possible, to set things so that the bootup proceeds to completion without the need to sit by the box to provide my password. 

I saw a mention in another thread that the thing to do is to disable 'auto' login. I tried that but it was worse - a small dialogue asked for user name as well as password and the lower half of the screen was filled with a virtual keyboard and the process seemed stalled until I completed the credentials.

Is it possible with KDE Plasma to get the boot completed and automatically logged into my account (I'm the only user) and how would I do it now without having to re-install yet again?

---

### Post by Nosphky on 2022-10-24
OK - I solved the puzzle but rather by accident. I spent quite a bit of time researching and found that auto login in KDE Plasma had been a problem for many people over the past 10 years. I tried many of the solutions offered but they didn't seem relevant to what I was seeing in 22.04. I also gathered that many people were also having annoying problems with KDE Wallet and that was also my case.

Because of my (solved) problems with graphics in 22.04 KDE Plasma, I am now on my 4th fresh installation and somehow, I missed the invite to set a password for KDE Wallet. It kept asking me to open the wallet for various apps but I didn't have the password. I tried my admin password and I tried an empty password but neither worked and I figured it was unlikely that I could guess the password. And I hoped to find some way of resetting Wallet other than making a 5th installation but my various researches were unfruitful.

To avoid the laborious login I mentioned at the bottom of my previous post, I went back into Settings and re-ticked the auto login box. Then came my breakthrough. Up came a dialog box informing me that I could prevent Wallet from intervening by setting a blank password. Since I was unable to change KDE Wallet's password, I created a new wallet (different name) with an empty password and set the new wallet to be used by default.

Now I boot up right into my account, the wallet makes no visible presence, my wifi connection gets established without my having to keep entering the WEP code. I can power up the desktop machine and get a coffee while it starts up.

---


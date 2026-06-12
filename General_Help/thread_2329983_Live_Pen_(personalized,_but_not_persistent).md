---
title: "Live Pen (personalized, but not persistent)"
date: 2016-07-06
forum: General Help
---

### Post by lordubu on 2016-07-06
Hi

I'd like to be able to create a persistent Linux live pen, then use the first session to personalize it (change keyboard layout to portuguese, install Keepass2, VLC, some Firefox plugins, etc) and then somehow  either stop it being persistent or make an ISO from the pen and create another pen from the ISO (non persistent this time).

Is this possible? The aim is to have a very secure live pen for online banking, but I can't just have a non persistent pen because then on each session I'd have to start from scratch (install keypass2, change keyboard layout, etc).

Thanks

---

### Post by QDR06VV9 on 2016-07-06
Moved to General...better fit

---

### Post by lordubu on 2016-07-09
It's solved! I created a pen for online banking the way I wanted it. This is what I did, following someone's suggestions on a forum (thanks YANCEK).

1) created a linux installation pen with Ubuntu 12.04 (because remastersys doesn't work with newer versions)
2) replaced the hard drive on my notebook with a blank ssd
3) installed Ubuntu 12.04 on the notebook with login password and encrypted HOME folder
4) updated installation and configured everything to my taste: installed Keypass2, changed wallpaper, inserted passwords for home and mobile networks, imported  browser favourites, configured browser according to my preferences, etc
5) went to [https://github.com/mutse/remastersys](https://github.com/mutse/remastersys) and followed instructions there, namely

sudo add-apt-repository ppa:mutse-young/remastersys
sudo apt-get update
sudo apt-get install remastersys remastersys-gtk

6) did the following in Terminal "sudo remastersys backup banking.iso"
7) transferred ISO to my windows PC (because I'm not very proficient in Linux) and created a pen with "Universal-USB-Installer" and the ISO.

And it worked. I now have a non persistent pen that is totally configured the way I want it, requires login and has my Keypass passwords file (.kdbx) inside an encrypted HOME folder.

---


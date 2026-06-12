---
title: "Midori Crashes but Midori Private Works"
date: 2018-05-22
forum: General Help
---

### Post by rbscairns on 2018-05-22
I first installed Midori browser using Synaptic Package Manager. All went well. When I go to Menu>Internet and click on Midori, the Midori window opens and then closes about 2 seconds later. Mindori Private works as expected.

I then decided to try and fix the Midori problem by reinstalling using command line as follows:
```
sudo apt-add-repository ppa:midori/ppa
sudo apt-get update
sudo apt-get upgrade
sudo add-apt-repository ppa:webkit-team/ppa
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install midori
sudo apt-get upgrade
```
Unfortunately, my Midori problem persists - Midori crashes after about 2 seconds yet Midori Private works.

Any help would be gratefully received and faithfully applied.

---

### Post by kerry_s on 2018-05-23
your better off with epipany-browser(aka:gnome web) i don't think midori has been worked on since 2016.

---

### Post by rbscairns on 2018-05-25
kerry_s, thank you for the suggestion. Yes, midori has not been worked on for over a year, however it is a relatively light-weight browser with some good functional characteristics. I tried epipany-browser and found it a bit to light and basic for what I would like.

---

### Post by Ahunt on 2018-05-25
Epiphany (Web browser) on Lubuntu 18.04 LTS is having its own problems right now. No video playback [as outlined in this other thread]("https://ubuntuforums.org/showthread.php?t=2392660").

---


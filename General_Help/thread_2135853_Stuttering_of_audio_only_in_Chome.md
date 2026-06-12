---
title: "Stuttering of audio only in Chome"
date: 2013-04-15
forum: General Help
---

### Post by sir_robert007 on 2013-04-15
Ive been having severe stuttering of audio in Chrome. It only happens in Chrome. Firefox and audio and video files on my computer play just fine. Could it be an issue with Flash? Or maybe I need to adjust my audio settings though there doesn't seen to be a way a can adjust my sound settings in Lubuntu.

This is a new problem so it may be an issue with updates to Chrome or flash. Any other ideas?

Im using Lubuntu 12.10

Comp Specs

Asus 900HD Netbook

CPU: 900mhz (Yeah I know its slow but surprisingly I can do alot with it)
RAM: 1GB
Hard Drive: 160 GB

---

### Post by vasa1 on 2013-04-15
Someone else has something similar: [http://ubuntuforums.org/showthread.php?t=2134594](http://ubuntuforums.org/showthread.php?t=2134594)

---

### Post by sir_robert007 on 2013-04-18
Ok thanks. Im gonna uninstall and reinstall Flash and see if that helps.

---

### Post by sir_robert007 on 2013-04-19
Ok so i uninstalled/reinstalled flash but that did not work. I then uninstalled and reinstalled Chrome. Still no luck. Im stumped here. Anyone have any other ideas?

---

### Post by Naygral on 2013-04-25
If you are using Version 26 of Chrome (the .deb from their website is this version), then add this line to the end of the command line of chrome (right-click the Chrome icon in the menu and go to properties):

--audio-buffer-size=2048

Restart your browser and test another video. This is a temporary fix until version 27 of Chrome where they have fixed this bug.

---

### Post by Psychobudgie on 2013-04-25
type chrome://plugins into the address bar and deactivate one of the two flashplayers you will see listed. Pepperflash is integrated with chrome and should be the latest of the two version wise. Once one is deactivated, restart chrome and the stuttering should be fixed.

---

### Post by vasa1 on 2013-04-25
> **Psychobudgie said:**
> type chrome://plugins into the address bar and deactivate one of the two flashplayers you will see listed. Pepperflash is integrated with chrome and should be the latest of the two version wise. Once one is deactivated, restart chrome and the stuttering should be fixed.
Well, if someone *wants* to use Pepper Flash, Naygral's suggestion is worth trying. I'm waiting for a Chrome version compatible with 13.04 and so I can't test the suggestion myself..

---

### Post by sir_robert007 on 2013-04-28
> **Naygral said:**
> If you are using Version 26 of Chrome (the .deb from their website is this version), then add this line to the end of the command line of chrome (right-click the Chrome icon in the menu and go to properties):

--audio-buffer-size=2048

Restart your browser and test another video. This is a temporary fix until version 27 of Chrome where they have fixed this bug.


Yay!! That fixed it! Thanks!!

---

### Post by Yellow Pasque on 2013-04-28
> **sir_robert007 said:**
> Ok so i uninstalled/reinstalled flash but that did not work.

For future reference, Chrome uses its own built-in version of Flash (not the system one). Please mark thread SOLVED.

---

### Post by timjam on 2013-05-02
This very nearly worked for me too... but I found in needed a larger buffer size value:

I used: > [COLOR=#000000]*--audio-buffer-size=4096*[/COLOR] and it worked great.

---


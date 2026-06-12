---
title: "netflix"
date: 2015-08-23
forum: General Help
---

### Post by huff2 on 2015-08-23
Hi all! Here's my question. Whenever I try and run Netflix, I get to the home netflix screen and it says that "in order to continue using Netflix, please update your browser." My firefox browser is up to date. How can I fix this?

---

### Post by monkeybrain20122 on 2015-08-23
The Windows : firefox version in user-agent-overrider is outdated. See point 2) of my post #2 [http://ubuntuforums.org/showthread.php?t=2291772](http://ubuntuforums.org/showthread.php?t=2291772)

---

### Post by www.pantz.org on 2015-08-23
Unfortunately Firefox is not supported by Netflix on Linux yet, unless you use a user agent switcher. To use it without changing your user agent you will  need to use Google's Chrome browser. Please see here for htm5 player requirements.  [https://help.netflix.com/en/node/23742](https://help.netflix.com/en/node/23742) They don't mention Linux or Firefox on this page but do mention Chrome. Chrome has the DRM extensions built in so Netflix can use the html5 player now even on Linux.  Also note you won't get anything higher than 720p res. This is a limitation by Netflix on the player through Chrome.

---

### Post by huff2 on 2015-08-23
I have the updated version of Chromium. It still says that I need to update my browser.

---

### Post by QIII on 2015-08-23
Hello!

Chromium is not Chrome.  Chromium is an open source version which lacks some of the proprietary features of Google Chrome.

You may either use Google Chrome, or add pepperflash to Chromium.  It has been a while, but I believe that can still be accomplished with the following command in the terminal:

```
sudo apt-get install pepperflashplugin-nonfree
```.

Let us know if that doesn't resolve this for you.

Firefox, by the way, can be used for Netflix.  It requires the addition of a few other items and, in my personal opinion, it is more trouble than it is worth.

---

### Post by huff2 on 2015-08-23
adding the pepperflash plugin didn't resolve the issue. How do I go about installing Chrome?

---

### Post by huff2 on 2015-08-23
Downloading and installing the latest version of Chrome hasn't resolved the issue either.

---

### Post by monkeybrain20122 on 2015-08-23
> **QIII said:**
> Hello!

Chromium is not Chrome.  Chromium is an open source version which lacks some of the proprietary features of Google Chrome.

You may either use Google Chrome, or add pepperflash to Chromium.  It has been a while, but I believe that can still be accomplished with the following command in the terminal:

```
sudo apt-get install pepperflashplugin-nonfree
```.

Let us know if that doesn't resolve this for you.

Firefox, by the way, can be used for Netflix.  It requires the addition of a few other items and, in my personal opinion, it is more trouble than it is worth.

pepperflash has nothing to do with Netflix. Chrome plays Netflix with HTML5 (out of the box) but Chromium wouldn't work because the HTML5 stream is drmed.

---

### Post by QIII on 2015-08-23
I realize that Chrome plays Netflix OOTB, which is why I use it for Netflix.  As I said, chromium lack some of the proprietary components.

My apologies for not realizing that chromium now requires widevine for DRM rather than pepperflash -- seeing as Netflix now uses HTML5.  As I said, it has been a while.

---

### Post by yancek on 2015-08-23
> Downloading and installing the latest version of Chrome hasn't resolved the issue either. 				

You need to give a little more info.  Which of the four options at the google-chrome site below did you select?  Are you able to use google-chrome to surf the web otherwise?  What specifically happens when you go to Netflix?  You should see a message usually there is a Netflix code.  Any google-chrome version 38 or newer should work.

---

### Post by jim_deadlock on 2015-08-23
> **www.pantz.org said:**
>  Also note you won't get anything higher than 720p res. This is a limitation by Netflix on the player through Chrome.

Does this mean I've been paying extra for HD all this time for nothing? Or is that a different thing? This is confusing...

---

### Post by huff2 on 2015-08-23
I'm using Netflix desktop and Chrome browser works fine.

---

### Post by huff2 on 2015-08-23
Well ... I went directly to netflix.com and that worked just fine. I suppose I won't use Netflix Desktop anymore. I'll call this one solved.

---

### Post by www.pantz.org on 2015-08-24
> **jim_deadlock said:**
> Does this mean I've been paying extra for HD all this time for nothing? Or is that a different thing? This is confusing...

720p and 1080p are HD,  If your paying for the HD w/2 screens then your not paying extra. Your paying for exactly what your getting which is 720p which is HD.  Chrome on LInux might be limited to 720p, but your getting the part of the HD your paying for. No worries. Just be nice to get 1080p because we are paying for it. Not sure what Netflix deal is with the limitations. I believe it has something to do with the content owners and their fears of pirating. Html5 can totally do 1080p (look at YouTube). So this is obviously Netflix being required to dial the resolution back to 720p. Let's hope this gets cleared up in the near future.

---


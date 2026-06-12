---
title: "transfer songs from i-pod to ubuntu"
date: 2008-02-12
forum: General Help
---

### Post by himperfectself on 2008-02-12
Hello :)
I am writing on behalf of my son who is an incarcerated inmate and does not have internet access to post this question.  He uses Feisty Fawn Ubuntu and needs help transferring tunes from i-pod (actually it is a GTX pod), from the player to his computer without losing the songs on the i-pod.  Thanks for your help.

---

### Post by apetresc on 2008-02-12
What has he tried so far? Rhythmbox, as far as I know, should be able to read songs off the iPod right out of the box. Just plug the iPod in, start Rhythmbox, add the iPod as a media device (if it doesn't autoload it itself), and just browse the library.

---

### Post by himperfectself on 2008-02-12
Thank you, Adrian.  Is Rhythm Box something that  would have come with his Ubuntu install?  (He used alternate install from CD as they have no internet. ??) Or, is this Rhythm Box something that must be purchased?:)

---

### Post by apetresc on 2008-02-12
> **himperfectself said:**
> Thank you, Adrian.  Is Rhythm Box something that  would have come with his Ubuntu install?  (He used alternate install from CD as they have no internet. ??) Or, is this Rhythm Box something that must be purchased?:)

:) No, it doesn't have to be purchased -- all of the software in Ubuntu is 100% free (legally). However, if he used the alternate install CD, it does need to be installed separately. It's very easy though, just type at a terminal:
```
sudo apt-get install rhythmbox
```
(I assume he's running Gnome. If he's running KDE, then replace "rhythmbox" with "amarok")

---

### Post by ptn107 on 2008-02-12
It doesn't matter which CD you use to install, desktop or alternate.  They both come with the same suite of software.  The alternate CD is just a means to install on computers running older hardware, or to install Ubuntu under more advanced installation scenarios.

Using either method, both will have Rhythmbox already installed.  You can start Rhythmbox by going to* Applications -> Sound & Video -> Rhythmbox*.

What version of Rhythmbox you have depends on the version of Ubuntu your running:

Ubuntu 7.10 Gutsy Gibbon - Rhythmbox 0.11.2
Ubuntu 7.04 Feisty Fawn - Rhythmbox 0.10.0 (but you can upgrade to Rhythmbox 0.11.2 by enabling the feisty-backports repository)

---

### Post by himperfectself on 2008-02-12
Thank you so much for your expertise and help.  i will mail this to him tomorrow.

---

### Post by himperfectself on 2008-02-14
Thank you for your replies to initial question; during phone call from my Son he indicated that he wants to **copy all of the songs from the i-pod to his computer so that they are always there.**  Does RhythmBox have the ability to transfer or copy the music to the computer, permanently, without also losing the songs on the I-pod ?  Thank you for your help

---


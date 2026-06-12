---
title: "resolution problem"
date: 2008-03-11
forum: General Help
---

### Post by uknowhoo138 on 2008-03-11
First I would like to point out I am newb to ubuntu. Having said that after making the switch to ubuntu was painless so far everything worked fine. Then yesterday I returned home from work and my resolution was 640x480 and I couldn't change it when before I had one that suited me better. Then I decided to go to the setting for video card and change from geforce to a different selection under geforce which was geforce followed by a word I cannot remember. After that pc told me log off and changes will take place so I did hoping I would be able to get better resolution only to get no gui at all. So now I am using the live cd to make this post. Video card is geforce 2 mx400 and I am using the gutsy release of ubuntu.

---

### Post by Rocket2DMn on 2008-03-11
reboot into the recovery kernel (second option on the GRUB screen) and run
```
dpkg-reconfigure xserver-xorg -phigh
```
Then restart the computer into normal mode with
```
reboot
```
That should reset your video stuff to the default, which you said worked.

---


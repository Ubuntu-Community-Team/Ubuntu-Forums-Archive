---
title: "&quot;Don't do Nothing&quot; when I close my laptop's screen"
date: 2014-12-28
forum: General Help
---

### Post by mrat2 on 2014-12-28
I have an external screen for my laptop that i use to watch some movies.
I want to configure in my Lubuntu 14.10 to don't do nothing when i close it. 'Cause everytime that i do it, black screen, and music or whatever stops. It's annoying to use it opened.

I readed about "gconf-editor" but damn, it doesn't exist in Lubuntu! Please, any alternative to fix it?

PD: New in the forum, spanish speaker, sorry for my english! xD

---

### Post by dragonfly41 on 2014-12-28
I'm not a Lubuntu user ... but does this help you ...

[http://ubuntuhandbook.org/index.php/2013/12/change-behavior-when-lid-is-closed/](http://ubuntuhandbook.org/index.php/2013/12/change-behavior-when-lid-is-closed/)

---

### Post by mrat2 on 2014-12-28
Mmmm no, sorry it doesn't worked. 
I don't know why this is happening, i had previously Crunchbang Linux installed in this computer and when i used to close the lid, it didn't do nothing! So, i can't understand, Crunchbang and Lubuntu uses LXDE and work differently when the lid is closed

---

### Post by dragonfly41 on 2014-12-28
Here are more suggestions ..

[http://askubuntu.com/questions/71033/closing-the-lid-isnt-toggeling-standby-anymore-after-update-in-lubuntu-how-can](http://askubuntu.com/questions/71033/closing-the-lid-isnt-toggeling-standby-anymore-after-update-in-lubuntu-how-can)

[http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid](http://askubuntu.com/questions/15520/how-can-i-tell-ubuntu-to-do-nothing-when-i-close-my-laptop-lid)

Again, I don't use Lubuntu and I don't have a second screen to try these suggestions.

---

### Post by kalehrl on 2014-12-28
You need to:
```
 nano /etc/systemd/logind.conf
```
Uncomment HandleLidSwitch entry and set it to 'ignore' like this:
```
HandleLidSwitch=ignore
```
Restart systemd-logind:
```
service systemd-logind restart
```
Also, if you have a power manager such as xfce-power-manager, go to its options and select 'do nothing' in 'when laptop lid is closed' option.

---

### Post by mrat2 on 2014-12-28
Damn guys, i love you.

It worked, the problem was that i forgot to uncomment the line.
I made all the changes but it wouldn't worked being commented, so thanks! Cya!

---


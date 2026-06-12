---
title: "Can't Install Any Operating Systems"
date: 2013-10-20
forum: General Help
---

### Post by QEdCnNK on 2013-10-20
So the other day I tried to install XP and I screwed something up so I aborted the mission and restarted and I loaded up into Lubuntu. Now, I've been trying to install Xubuntu and I just get to the loading screen where it shows the bar sliding back and forth and nothing changes. It stays like that forever. I've also tried using elementryOS and it did the same thing but with the elementaryOS logo. How do I fix this? Also, here is a picture of my partitions if that helps. I'm kind of a newb.

[IMG]http://i.imgur.com/4W09jfa.jpg[/IMG]

---

### Post by Impavidus on 2013-10-21
So Lubuntu boots but you cannot boot the Xubuntu live disk. How much RAM have you got? If it's not enough, you may be using swap which makes the computer very slow.

Your hard drive is too small to have a complete installation of Lubuntu and Xubuntu in parallel and still have a decent amount left for storage. The primary difference between them is the desktop environment. You could install the xubuntu desktop on top of your lubuntu and select which one to use on log-on: **sudo apt-get install xubuntu-desktop**. Also see [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

---


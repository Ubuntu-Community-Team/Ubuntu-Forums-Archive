---
title: "Okular Menu issue"
date: 2019-04-12
forum: General Help
---

### Post by cmcanulty on 2019-04-12
Yesterday I installed okular on 13 library computers all running Xubuntu 18.04. All went well except for one computer. The problem computer had one user with okular looking fine. The other user had no menu bar in okular. I tried various fixes including ctlr+m, reinstalling and even purging okular and no luck. I even copied the okularrc file from another computer, all with no luck. Then I tried a fix from a a tech site 
[http://terokarvinen.com/2019/fix-lost-or-empty-menu-on-okular-thunderbird-and-krita-sudo-apt-get-purge-indicator-appmenu]("http://terokarvinen.com/2019/fix-lost-or-empty-menu-on-okular-thunderbird-and-krita-sudo-apt-get-purge-indicator-appmenu")
so that involved issuing this command
```
sudo apt-get purge indicator-appmenu
```
so eureka I thought it was fixed until I looked closely and the menu bar was back but now had 3 duplicate menus for NoText. Now is there anything I can do to fix the menu. I looked in all the okular files and couldn't find a way to edit those entries. And the configure toolbar doesn't fix it. Thank you

---


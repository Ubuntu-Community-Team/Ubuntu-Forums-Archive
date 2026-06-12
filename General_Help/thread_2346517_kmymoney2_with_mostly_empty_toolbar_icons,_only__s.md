---
title: "kmymoney2 with mostly empty toolbar icons, only ? showing."
date: 2016-12-15
forum: General Help
---

### Post by ajgreeny on 2016-12-15
I am using Xubuntu 16.04 and have for a very long time used kmymoney2 for my personal finance and banking application.
It runs with no real problems except that since my move to 16.04 (by clean install) the kmymoney2 toolbar shows almost no icons; just ?s are shown, as in the screenshot. In 14.04 everything showed as it should.

I have searched hard to see if anyone has solved this but can find nothing.
Anybody got any clues about how to get the toolbar looking as it should.

---

### Post by ajgreeny on 2016-12-15
More searching has solved this for me.
```
sudo add-apt-repository ppa:claydoh/kmymoney2-kde4
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kmymoney
```
now gives me version 4.8.8 which has all icons showing as referred to in the bug at [https://bugs.launchpad.net/ubuntu/+source/kmymoney/+bug/1521689](https://bugs.launchpad.net/ubuntu/+source/kmymoney/+bug/1521689)

I have no idea why I could not find that previously; obviously I must have used different search terms.

---

### Post by oldfred on 2016-12-15
Thanks for posting.

It reminded me. 
I am sure with my older install I used that ppa.
And when I installed 16.04 as my main working install and 4.8 came out, I wanted to update. But the ppa was not yet updated and I forgot all about it.
Now updated.

---

### Post by ajgreeny on 2016-12-16
Did you have the same very annoying icon problem as I did?

---

### Post by oldfred on 2016-12-16
No I did not.

But I use Ubuntu with fallback/gnome panel. My old monitor is 4:3 and having the top & bottom bars works, but I have not tried kubuntu for ages. Just installed a copy of Mate on another partition just to see what it is. But so used to gnome panel, difficult to change.

Adding kmymoney & a couple other k apps adds a lot of supporting programs.

---

### Post by ajgreeny on 2016-12-16
I have been on Xubuntu and not used Kubuntu for a very long time as well, but I still use both kmymoney2 and digikam from the KDE stable, so I'm aware that KDE apps pull in a lot of KDE and QT packages.

I tried Kubuntu as a VM in VBox recently and hated when it compared with Xubuntu, but that's all part of the joy of Linux; so many options to choose from!

---


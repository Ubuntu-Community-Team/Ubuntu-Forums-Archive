---
title: "Flash player needed message"
date: 2014-10-16
forum: General Help
---

### Post by michael-piziak on 2014-10-16
After upgrading to 14.x lts, most of the youtube movies play for me.  However, some times I come across one like this one that says Flash Player is needed:  [https://www.youtube.com/watch?v=Jo9t5XK0FhA](https://www.youtube.com/watch?v=Jo9t5XK0FhA)

Update:  This only occurs in Chromium Web Browser.

Perhaps I should go back to Chrome - perhaps someone could tell me the terminal command to reinstall it.

---

### Post by deadflowr on 2014-10-16
Did you install pepperflashplugin-nonfree?
Chromium now needs the pepperflash plugin, and not the normal flash plugin which you would get from either flashplugin-installer, or ubuntu-restricted-extras.

---

### Post by ajgreeny on 2014-10-16
Chrome and chromium no longer work with NPAPI plugins so you must install the pepperflashplugin-nonfree mentioned by deadflowr.
Installing the adobe flash packages that we used to use will not work with those two browsers any more.

Incidentally, you can also install the same plugin in Firefox now with the help of a freshplugin installer available from a ppa, which I have done already on one of my machines and it seems to work well.  I am not on that machine at the moment and can not find the ppa I used; I will find it *asap* and report back.

---

### Post by deadflowr on 2014-10-16
> Incidentally, you can also install the same plugin in Firefox now with  the help of a freshplugin installer available from a ppa, which I have  done already on one of my machines and it seems to work well.  I am not  on that machine at the moment and can not find the ppa I used; I will  find it *asap* and report back. 				

This?
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

---

### Post by ajgreeny on 2014-10-17
> **deadflowr said:**
> This?
[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

Thanks, mate.

I don't know why I couldn't find it this time; it was so easy to find a few days ago when I enabled it on the other machine.

It's certainly worth a try as you can install it without uninstalling the normal plugin; you just need to disable the 11.2 version in the Tools->Add-ons page of FF.

EDIT:
Just a quick update for my main installation of Xubuntu 12.04.5.

I have just this minute added the pepflashplugin as shown in that webupd8 page to my FF in that main machine and though it shows as installed and enabled in the Tools->Add-ons page of FF it does not work at all.
It did work fine on my 14.04 version of Xubuntu, as I said above.  

Obviously not really ready for 12.04 just yet.

---


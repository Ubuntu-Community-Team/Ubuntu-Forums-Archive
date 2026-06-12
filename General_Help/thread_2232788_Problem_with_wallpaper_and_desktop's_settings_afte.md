---
title: "Problem with wallpaper and desktop's settings after installing thunar"
date: 2014-07-04
forum: General Help
---

### Post by coditoter on 2014-07-04
Hello geeks!
I've installed thunar and made it as my default file manager using [that script]("https://help.ubuntu.com/community/DefaultFileManager#Script_to_change_Thunar_to_be_the_default_file_manager"). Everything works quite nice but I cannot use my desktop settings. I'm unable to change my wallpaper too. Screenshots attached.
Is there any solution? I like PCManFM but, unfortunately, it can't fully support dropbox.

---

### Post by Bucky Ball on 2014-07-04
Have a look in Synaptics for 'desktop'. You're probably using xfdesktop4 or lxdesktop (if there is such a thing). Whatever desktop manager you're using, open a terminal and, say it is xfdesktop4, simply type 'xfdesktop4' in and hit return. 

Do you get normal desktop settings and icons now?

I'm presuming you're using Lxde or Lubuntu from the looks of your screenshot. Please confirm, and also the release number. Thanks.

PS: You really don't need that script. That is a Ubuntu fix, anyhow, possibly old and for Gnome rather than lxde. I've only just started using lubunutu, but you go to preferences and it's in one of the options there, possibly starting with 'Session ***' something, from memory. Not on that box now. You can set default apps in there. No need for scripts.

---

### Post by ibjsb4 on 2014-07-04
Some interesting reading about pcmanfm.

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/696302](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/696302)
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dropbox+pcmanfm&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=dropbox+pcmanfm&sa=Search&cof=FORID:9)

---

### Post by coditoter on 2014-07-08
O, sorry for no answer.
Well, I've installed Xubuntu with Xfce and thunar default but IMHO it's slower. So I want to use Lubuntu again.
I' ll instal Lubuntu and then report. MODs -> So please, don't make topic as closed.
And about the script. Well, I installed thunar but I couldn't change it as defalut manager using sessions settings - no option 'thunar manager' available. Only after using the script sth changed.
 But, well I'll try again & report soon.

---

### Post by Bucky Ball on 2014-07-08
> **coditoter said:**
> MODs -> So please, don't make topic as closed.


We only close threads in accordance with forum rules and guidelines. Otherwise, you mark your thread as solved when it is by using Thread Tools at the top right of the page. We still don't close it then and folk are free to continue discussing (sometimes there is much interesting and educational discourse post-solution). ;)

Be aware, though, that after your upcoming Lubuntu install, if you have problems unrelated to the thread title, you will greatly improve your chances if you post a new thread rather than posting a new support request on this one. Good luck.

---


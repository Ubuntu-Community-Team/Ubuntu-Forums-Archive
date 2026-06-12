---
title: "[SOLVED] Enable Google Search From Shortcut Key in KDE on (k)Ubuntu"
date: 2008-06-29
forum: General Help
---

### Post by uclalinux on 2008-06-29
[http://www.howtogeek.com/howto/ubuntu/enable-google-search-from-shortcut-key-in-kde-on-kubuntu/](http://www.howtogeek.com/howto/ubuntu/enable-google-search-from-shortcut-key-in-kde-on-kubuntu/)

I found this on How-to Geek but I can't get it to work in Gnome using Firefox, can someone tell me if there is a way. 

Thanks

---

### Post by kuja on 2008-06-29
For that command it references (dcop) to work, you need to install kdelibs4c2a.

---

### Post by uclalinux on 2008-06-29
I have **kdelibs4c2a** install...

---

### Post by kuja on 2008-06-29
Ah, now the thought hits me. It had almost slipped my mind that *Firefox doesn't use dcop*

Let me check real quick if it uses dbus perhaps .... Hmm, seems not. 

Rather than taking this route, I think it'd be easier/actually possible to use the program Katapult. If interested, install Katapult, start it, hit alt+space to use it, when it's up, press ctrl+c, under catalogs, select google, and change it to something shorter, I've shortened it to "g" myself. Now, I believe it launches KDE's default web browser to google it, so you'll want to change that to firefox if it isn't already set. The most direct way to do that would be to hit alt+f2 then type "kcmshell defaultapplication", hit enter, go to the web browser tab, and change it to custom, "firefox", click apply and exit that, and you should be good to go. Hope this helps.

---

### Post by uclalinux on 2008-06-30
Ok, so i wrote my own.

** UPDATED 7/26/2008, NEED TO INSTALL xsel, "sudo aptitude install xsel" **
 

In my **/home/uclalinux/scripts ** I added **googlesearch.sh**
which is 
```
#!/bin/bash 

selc=`xsel -o | sed -e "s/ /+/g"`

echo "$selc"

website="http://www.google.com/search?num=30&hl=en&safe=off&q=$selc&btnG=Search"

firefox "$website"
```

now >  chmod 777 ~/scripts/googlesearch.sh
Now I download the attached google image and move it to my  **/home/uclalinux/.icons/google.png**

I went to the panel on the top, Right Click > Add to Panel > Custom Application launcher.  

```
Type: Application
Name: Google Search 
Command: /home/uclalinux/scripts/googlesearch.sh
Comment: Highlight text anywhere and it will be search in Google
```

If you click on the spring icon you can replace it with the google PNG which look nice on the panel.[ATTACH]75761[/ATTACH]

---


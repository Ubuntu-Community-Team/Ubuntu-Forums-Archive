---
title: "Can't launch magnet link in transmission"
date: 2013-06-29
forum: General Help
---

### Post by Heinzelmannchen on 2013-06-29
I have ubuntu 13.04 installed and am using firefox. I'm confused why i can't launch transmission as the app of choice. It worked fine on my previous installs. I couldnt find any information on the subject and this is my first time encountering it. I've already reinstalled both firefox and transmission to no avail. When hitting get magnet a box pops up prompting me to choose application. Normally transmission would be listed here. By searching for the application i can't find it. It doesn't show any applications to choose just files.

---

### Post by royph on 2013-06-29
I am having the exact same problem with a new install (New HD) of 12.04. Previously it worked fine on the same computer. I did install Deluge and that works on some sites but not all. Looking forward to help as I was just getting ready to post same issue.

---

### Post by fantab on 2013-06-29
> **Heinzelmannchen said:**
> ... 
When hitting get magnet a box pops up prompting me to choose application. Normally transmission would be listed here. By searching for the application i can't find it. It doesn't show any applications to choose just files.

In the 'box that pops up' choose /usr/share/applications/transmission. You may have to select it manually. Tell us if that helps.

---

### Post by royph on 2013-06-30
Heinzelmannchen, I am the person who posted he had the same problem and here's hpw I fixed it, at least it worked for me.

In Firefox click Edit then Preferences, go to Magnet and click on Use Other click on File System then "usr" then "bin" and find Transmission or Transmission-gtr. You can then set Transmission as default.

Hope it works for you as well.

---

### Post by Horbo on 2013-06-30
A work-around (not a solution) is to drag magnet links from your browser window into an open transmission window.

---

### Post by Heinzelmannchen on 2013-07-07
> **fantab said:**
> In the 'box that pops up' choose  /usr/share/applications/transmission. You may have to select it  manually. Tell us if that helps.
clicked transmission-gtk.desktop and nothing happens


> **royph said:**
> Heinzelmannchen, I am the person who posted he had the same problem and here's hpw I fixed it, at least it worked for me.

In Firefox click Edit then Preferences, go to Magnet and click on Use Other click on File System then "usr" then "bin" and find Transmission or Transmission-gtr. You can then set Transmission as default.

Hope it works for you as well.

Followed this and i only see transmission gtk not gtr. I don't know if that's the problem.

---

### Post by Heinzelmannchen on 2013-07-07
I've also tried the following unsuccessfully. :( I don't know what it is i am missing...


> * Type about:config into the address bar and press Enter.
* Right-click -> New -> Boolean -> Name: network.protocol-handler.external.magnet -> Value -> true
* Right-click -> New -> String -> Name: network.protocol-handler.app.magnet -> Value -> /usr/bin/transmission
* Ensure network.protocol-handler.expose-all is set to true

---

### Post by markbl on 2013-07-07
I just edit my ~/.local/share/applications/mimeapps.list by hand. Not very sophisticated but has always worked for me!

---

### Post by Heinzelmannchen on 2013-07-08
Still can't get these magnet links to work. I've tried multiple tutorials with no luck. I'm thinking a reinstall of ubuntu is my best bet at this point because i have no idea why they aren't working. Both transmission-gtk.desktop and deluge-gtk.desktop don't work. 

[Tutorial ]("http://gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command &quot;/usr/bin/transmission %s&quot; gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true")(similar to many responses)

> **markbl said:**
> I just edit my ~/.local/share/applications/mimeapps.list by hand. Not very sophisticated but has always worked for me!

Mind telling me how to do that? I can only access ~/.local/share/  there doesn't seem to be an applications folder. 


Do you guys recomend i try upgrading to ubuntu 13.1 and see if the problem persists?

---

### Post by markbl on 2013-07-08
> **Heinzelmannchen said:**
> 
Mind telling me how to do that? I can only access ~/.local/share/  there doesn't seem to be an applications folder.
Create the directory and file. Copy the format from /usr/local/share/applications/default.list for the torrent entries. Uncle Google has a zillion links on this stuff.

---

### Post by Heinzelmannchen on 2013-07-09
> **markbl said:**
> Create the directory and file. Copy the format from /usr/local/share/applications/default.list for the torrent entries. Uncle Google has a zillion links on this stuff.
I created the directory and file with no luck on firefox. I know i'm still a noob to ubuntu and linux in general but i'm competant enough to follow a tutorial. Trust me i've been googling this problem for a week.(also viewed the other tutorials on this site) All the results are giving me the same solutions which is why I’m so confused to why it isn't working still. I've narrowed it down to being a problem with firefox though as magnet links on chrome work. 

For now at least i have a few temporary fix but would like to find a solution still if anyone can help.

---

### Post by palynch32 on 2013-08-02
Worked a treat for me thanks royph

---

### Post by ottobrito on 2013-09-08
Thank you so much ! Finally the solution, it really worked for me.

---

### Post by morphw2 on 2013-09-21
the application can be found under /usr/bin. When the box pops up, search there (/usr/bin) and you will find transmission-gtk. Open it and choose it.

---

### Post by ashoke2 on 2014-02-18
This helped me ... Thanks!

---


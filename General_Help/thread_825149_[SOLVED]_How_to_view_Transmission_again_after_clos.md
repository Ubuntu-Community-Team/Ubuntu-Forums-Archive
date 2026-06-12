---
title: "[SOLVED] How to view Transmission again after closing?"
date: 2008-06-10
forum: General Help
---

### Post by GammaPoint on 2008-06-10
So I use the Transmission torrent client that comes with a standard Ubuntu install. The program works fine for me.  Problem is is that if I close the window (by clicking the 'X') then transmission still runs but I can no longer see the display.  Thus if I go back into the application menu and click on transmission again it tells me that 'another copy of transmission is already running'.

Of course I can simply 'kill' the old tranmission and start transmission after doing so, but is there a way that I can see the transmission gui after closing it somehow? When I used Fedora Transmission would make a little icon at the top right of my screen that I could always click on.  Why don't I have that in Ubuntu? Is there an option somewhere that will allow for that?

Thanks!

---

### Post by Vivaldi Gloria on 2008-06-10
It makes a little icon on the panel.

---

### Post by Vivaldi Gloria on 2008-06-10
Here is a snapshot.

---

### Post by Sinkingships7 on 2008-06-10
So just click the icon and it will appear again.

---

### Post by GammaPoint on 2008-06-10
As I said, I don't get an icon so I can't click on it.  

[[IMG]http://img73.imageshack.us/img73/2939/noiconuv7.th.png[/IMG]](http://img73.imageshack.us/my.php?image=noiconuv7.png)

Here is a screenshot of my desktop. As you can see I have transmission open and no icon.

---

### Post by Tom Mann on 2008-06-10
Can you find it in your window list when you use alt-tab? If not, I suggest going System > Administration > System Monitor, clicking the processes tab, right clicking transmission in the list, and select kill process. Then restart it from the menu.

EDIT: Seeing as you can already get the window back up, try checking your preferences and make sure "Show an icon in the system tray" is selected.

EDIT 2: Right click the top bar, and select "Add to panel...", then drag the notification area selection to that bar.

---

### Post by GammaPoint on 2008-06-10
> **Tom Mann said:**
> 
EDIT 2: Right click the top bar, and select "Add to panel...", then drag the notification area selection to that bar.

That was it. I didn't have that up there for some reason.  Thanks!

---

### Post by SunTzuWarmaster on 2008-06-30
Thanks!  Was having the same issue for the same reason.  Also, 197 updates are available :O

---


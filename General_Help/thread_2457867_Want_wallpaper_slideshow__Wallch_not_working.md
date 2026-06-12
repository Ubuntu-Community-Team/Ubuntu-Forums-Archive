---
title: "Want wallpaper slideshow || Wallch not working"
date: 2021-02-11
forum: General Help
---

### Post by linuxyogi on 2021-02-11
Hi,
I am using Lubuntu 20.04. I want the wallpaper to change based on number of 15-20 images. I want the change to happen in 10 mins. 
I have installed Wallch but its not working. It doesnt set any wallpaper whatsoever. I am attaching a screenshot.
If you want to suggest any other app please make sure its in the official repos coz I don't add PPAs
[ATTACH=CONFIG]287945[/ATTACH]
(Click to enlarge)

Edit: I just watched a video on Youtube which shows Shotwell to achieve wallpaper slideshow. I did exactly what the video shows but the wallpaper never changed.

---

### Post by dragonfly41 on 2021-02-11
I don't need to change background image but as an exercise I found this ..

[https://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity](https://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity)

And intuitively I would launch the next image through a cronjob calling script every 10 mins. The script will need to run through a list.

---

### Post by Impavidus on 2021-02-11
I think that using Lubuntu instead of Ubuntu makes a difference. I made my own wallpaper changing script, using a cronjob running every 15 minutes, using```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitorLVDS-1/workspace0/last-image -s "$HOME/path/to/file.jpg" 2>> $logfile
```
but as you can see that's for Xubuntu.

---

### Post by Holger_Gehrke on 2021-02-11
Modern desktops all put a desktop window on top of the actual root window. The mechanisms to set the background of that window are different from one desktop to the other. wallch is for Gnome 3, XFCE, LXDE and Mate according to the README on [https://sourceforge.net/projects/wall-changer/files/](https://sourceforge.net/projects/wall-changer/files/). LUbuntu uses LXQT ...

According to the [LUbuntu manual]("https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html"), there is a wallpaper changer built into LXQT, unless this is a new feature in 20.10 you should just try that.

Holger

---

### Post by ajgreeny on 2021-02-11
I have only seen this used on Arcolinux, never on any of the Ubuntu family, and in Arcolinux I always removed it as it annoys me, but the package ***variety*** did the job in Arcolinux using the Xfce desktop.
It is in the repos of 20.04 and I presume it is in other numbered versions as well so will be easy to install.
As I always removed it and never used it I can not help with any details about its configuration or anything else about the use of this.
Incidentally, Xubuntu has an inbuilt desktop changer which is set in Desktop Settings from a right click on the desktop.

---

### Post by guiverc on 2021-02-11
The easiest way is using the SLIDESHOW feature of LXQt desktop.

[https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html?highlight=slideshow](https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html?highlight=slideshow)

ps:  If were you asked a question recently (*last night my local time*) on IRC, the answer was provided seconds after you left; actually a number were - check the irc logs.  Sorry, often it takes time for *ideal solutions* that we don't use ourselves to be remembered.

---

### Post by linuxyogi on 2021-02-12
> **guiverc said:**
> The easiest way is using the SLIDESHOW feature of LXQt desktop.
[https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html?highlight=slideshow](https://manual.lubuntu.me/stable/3/3.2/3.2.5/desktop.html?highlight=slideshow) 
Thanks a lot. This ^^ is the solution. It was inbuilt all this time & I like an idiot was installing apps for it.

---


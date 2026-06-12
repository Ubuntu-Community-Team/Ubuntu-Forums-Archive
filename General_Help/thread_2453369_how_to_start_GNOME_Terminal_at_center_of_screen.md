---
title: "how to start GNOME Terminal at center of screen?"
date: 2020-11-09
forum: General Help
---

### Post by ardouronerous on 2020-11-09
[https://i.ytimg.com/vi/s00FvXA9V7s/maxresdefault.jpg](https://i.ytimg.com/vi/s00FvXA9V7s/maxresdefault.jpg)

Running Xubuntu 20.04.

GNOME Terminal starts like this. I'd like for it to start at the center of the screen instead. My screen resolution is 1366x768. How can I do this, thanks.

---

### Post by ajgreeny on 2020-11-09
Running Xubuntu but using gnome-terminal; why?

Your image looks more like a gnome DE so tell us more.

Please do not add large images to posts.
Some users on small screens or those with limited or expensive network costs will be unable to see such images.
Use the attachment facility in the Reply to post toolbar, the paperclip, which will add a thumbnail to the post which users can open if they wish to.

---

### Post by ardouronerous on 2020-11-09
> **ajgreeny said:**
> Running Xubuntu but using gnome-terminal; why?

Your image looks more like a gnome DE so tell us more.

GNOME Terminal has features that I like over XFCE Terminal, like relaunching code after it's done executing.

It's not my image, I used this image as an example only.

---

### Post by ardouronerous on 2020-11-09
> **ajgreeny said:**
> Please do not add large images to posts.
Some users on small screens or those with limited or expensive network costs will be unable to see such images.
Use the attachment facility in the Reply to post toolbar, the paperclip, which will add a thumbnail to the post which users can open if they wish to.

Thanks for the heads up.

---

### Post by ajgreeny on 2020-11-09
> **ardouronerous said:**
> GNOME Terminal has features that I like over XFCE Terminal, like relaunching code after it's done executing.

It's not my image, I used this image as an example only.
Do you mean repeating the same command?

Xfce4-terminal does that just like all terminals by using the up cursor key.
If you mean something else I did not understand your comment..

---

### Post by ardouronerous on 2020-11-09
> **ajgreeny said:**
> Do you mean repeating the same command?

Xfce4-terminal does that just like all terminals by using the up cursor key.
If you mean something else I did not understand your comment..

I use GNOME Terminal for Speedtest CLI:

```
[Desktop Entry]
Version=1.1
Type=Application
Name=Speedtest CLI
Comment=Test your bandwidth throughput using speedtest.net
Icon=speedtest
Exec=gnome-terminal -t "Speedtest CLI" -e speedtest-cli
Categories=Network;
```

And I only click on "Relaunch" to retest my connection. But I want the terminal window to start up in the center of my screen than on the side.

---

### Post by ardouronerous on 2020-11-09
I've done my own research on this and I found this: [https://superuser.com/questions/15626/how-to-start-a-terminal-window-in-the-center-of-the-screen](https://superuser.com/questions/15626/how-to-start-a-terminal-window-in-the-center-of-the-screen)

```
gnome-terminal --geometry=114x32+0+0
```
```
gnome-terminal --geometry=90x20+400+300
```

However, I don't understand how they were able to get the numbers for the geometry or how to convert my screen resolution 1366x768 to these numbers.

---

### Post by ajgreeny on 2020-11-09
I think setting it for your own resolution will be partly by trial and eror.

The first two figures, 90X20, are the terminal size, width in characters x height in rows, and the second two, +400+300, are pixels away from the X and Y margins, ie, probably the left and bottom edges of the screen.

---

### Post by ardouronerous on 2020-11-09
After some trial and error, I managed to get my terminal window to the center.  Although, I wish there was a command that would center the window despite the resolution, so if I move to a new computer with different resolution, the terminal window would still appear center.

---


---
title: "menu bars have disappeared"
date: 2008-06-10
forum: General Help
---

### Post by micromachine on 2008-06-10
I'm running the newest version of Ubuntu, all upgraded and what not. The battery on my laptop died. When I charged it up and restarted Ubuntu both the top and the bottom menu bars had disappeared. I have rebooted twice and they haven't come back. How do I get them back?

---

### Post by tamoneya on 2008-06-10
go into terminal and type ```
sudo dpkg-reconfigure ubuntu-desktop
```

---

### Post by iaculallad on 2008-06-10
Press Ctrl+Alt+F1 to enter your terminal:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/panel
sudo pkill gnome-panel
sudo shutdown -r now
```

---

### Post by micromachine on 2008-06-11
Here is what happened when I tried these

[IMG]http://img.photobucket.com/albums/v48/sfeild/Screenshot.png?t=1213162120[/IMG]

---

### Post by iaculallad on 2008-06-11
> **micromachine said:**
> Here is what happened when I tried these

[IMG]http://img.photobucket.com/albums/v48/sfeild/Screenshot.png?t=1213162120[/IMG]

That should be: sudo apt-get install ubuntu-desktop

and

This should be a ~ not a -

sudo rm -rf ~/.gconf/panel

---

### Post by tamoneya on 2008-06-11
are you using ubuntu or a version of ubuntu(kubuntu, xubuntu)?  Also the command for installing a package is ```
sudo apt-get install ubuntu-desktop
```You just missed the "install" part.

---

### Post by micromachine on 2008-06-12
Alright, I think I must have accidentally uninstalled the desktop when I was trying to delete something else. So I installed the desktop correctly and rebooted and that didn't work. Then I ran though all of your suggestions again (I was really careful typing this time) and the menu bars are not back. 

I'm running hardy ubunutu.

---

### Post by tamoneya on 2008-06-12
what happens when you type: ```
gnome-panel
```in terminal?

---

### Post by micromachine on 2008-06-12
> **tamoneya said:**
> what happens when you type: ```
gnome-panel
```in terminal?

hell yeah! that worked! Everything back to normal! Thank you!

---

### Post by wootah on 2008-06-12
> **micromachine said:**
> hell yeah! that worked! Everything back to normal! Thank you!

Make sure that you save your session or they might disappear on reboot!

[http://www.techotopia.com/images/b/bf/Ubuntu_desktop_session_options.jpg](http://www.techotopia.com/images/b/bf/Ubuntu_desktop_session_options.jpg)

You'll find this in System | Preferences | Session

---


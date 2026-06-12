---
title: "config file for session preferances, or else session help"
date: 2008-07-04
forum: General Help
---

### Post by Zopiac on 2008-07-04
i...um...messed this one up. in my main acccount (zopiac), i took of a bunch of stuff from my session properties, including tracker, evolution alarm notifier, and other stuff i thought i had no use for. however, i did NOT take off AWN or gnome-do, or pidgin, for that matter. i had all of those open when i went to 'save current session windows' or whatever, even, and when i re-logged in, NOTHING was open. i couldnt activate gnome-do, or even the Annotate plugin from Compiz. i can't even right-click on my desktop (my desktop has been unusable for a long time, and i liked it so i didnt try to fix it, but now i wish i had!!!). I decided i would ask what the configuration file for the session properties was, so i can either edit that or replace the one from my seconday account (gaming), which i am currently using.

1. What is the Config file?
2. How do i edit it, or should i just replace it w/ the Gaming one?
3. Are there other fixes?

Thank you!

---

### Post by Zopiac on 2008-07-07
several times it DID work, but i have absolutely no idea why. in the 15+ times i've tried to login, reboot, login, try again, etc., i havent been able to make it work like that one or two times.

---

### Post by Barriehie on 2008-07-07
Your session file would be **~/.gnome2/session   **So you could copy that file from your gaming account to your zopiac account and perhaps have something to start with.

Barrie

Edit: Or you could try editing the zopiac one; I wouldn't do it!

---

### Post by Zopiac on 2008-07-07
> **Barriehie said:**
> Your session file would be **~/.gnome2/session   **So you could copy that file from your gaming account to your zopiac account and perhaps have something to start with.

Barrie

Edit: Or you could try editing the zopiac one; I wouldn't do it!

thanks! i have it so that nothing but pidgin and gnome-do open, and it stopped working altogether. gnome-do is my menu (replacing menu bars and awn, etc.), with compiz plugins as window selectors (scale and shift switcher), and i plain want to have pidgin open at startup :P. you cant even have anything on the desktop, nor can right-click on it for a menu :) its very minimalistic; when i minimize my windows its like locking the screen, except i keep my wallpaper tray's wallpaper switching every minute! perhaps i accidentally told a neccessary instance to not open at startup, idk.

---

### Post by Barriehie on 2008-07-07
> **Zopiac said:**
> thanks! i have it so that nothing but pidgin and gnome-do open, and it stopped working altogether. gnome-do is my menu (replacing menu bars and awn, etc.), with compiz plugins as window selectors (scale and shift switcher), and i plain want to have pidgin open at startup :P. you cant even have anything on the desktop, nor can right-click on it for a menu :) its very minimalistic; when i minimize my windows its like locking the screen, except i keep my wallpaper tray's wallpaper switching every minute! perhaps i accidentally told a neccessary instance to not open at startup, idk.

Don't have all that stuff running on my machine.  Plain GNOME,  I like fast!  Let us know when and how you get it figured out.

Barrie

---

### Post by unutbu on 2008-07-07
All your GNOME configurations (I believe) are held in 4 directories: .config, .gconf, .gnome and .gnome2. 
Here are instructions for resetting your account so it should act like a new account. There are also instructions there for restoring those directories, so at worst you won't lose anything and nothing will have changed:

[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)

---

### Post by Zopiac on 2008-07-07
barrie: what does the ~/.gnome2 mean? /home/account/.gnome2? (btw, this is a temporary account, and so named it account ;) )there is no /home/account/.gnome2 folder...

edit: nevermind, it was hidden. i havent selected that setting yet in this account . . .

---

### Post by Zopiac on 2008-07-07
/home/account/.gnome2/session

this file does not exist, however, the one in /home/zopiac/,gnome2 does?

---

### Post by Barriehie on 2008-07-08
I think unutbu has perhaps the best solution posted prior.  I don't know enough to be able to tell you how to create a session file.  I'm sure someone here does though!

The **~** means **/home/*your account name*/** directory.

Barrie

Edit:  File names that start with a . are hidden.  You can set nautilus preferences to display them or ctrl-h will   toggle them visible.

---

### Post by Zopiac on 2008-07-08
> **Barriehie said:**
> Edit:  File names that start with a . are hidden.  You can set nautilus preferences to display them or ctrl-h will   toggle them visible.

k just didnt have that enabled, so didnt think if it. thx tho!

---

### Post by Zopiac on 2008-07-08
thank you so very much, unutbu! this fixed my problem perfectly (besides setting settings (?) again)!

---


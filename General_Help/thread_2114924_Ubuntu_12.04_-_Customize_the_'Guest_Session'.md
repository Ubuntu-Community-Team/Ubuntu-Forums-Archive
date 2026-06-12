---
title: "Ubuntu 12.04 - Customize the 'Guest Session'"
date: 2013-02-11
forum: General Help
---

### Post by collisionystm on 2013-02-11
Okay so here's the deal.

I have a computer running 12.04. I want to make use of the built in 'Guest Session' feature.

I only want to change 2 things.

1, the icons that show up by default on the unity launcher
2, the wallpaper.

Anyone who has used Guest-Session knows that it creates a temporary account and then purges it upon logging out.
The problem is, I cannot seem to find where it is pulling its default configuration from.

I tried doing some editing with dconf and tracing through the .bashrc files to no avail.

The only thing I saw after some googling was switching from lightdm to GDM and having scripts. I am hoping to avoid this because, frankly, that is just stupid. It must be pulling its configuration from somewhere.

In the mean time I'll keep ripping apart my ubuntu install to find the answer.

Thanks for any help you guys can offer!

---

### Post by Bufeu on 2013-02-11
[http://ubuntuforums.org/showthread.php?t=1566078](http://ubuntuforums.org/showthread.php?t=1566078) :)

---

### Post by collisionystm on 2013-02-11
> **Bufeu said:**
> [http://ubuntuforums.org/showthread.php?t=1566078](http://ubuntuforums.org/showthread.php?t=1566078) :)


Thanks!

I found this too

[http://askubuntu.com/questions/38331/how-to-change-default-launcher-icons-in-unity-for-a-new-user](http://askubuntu.com/questions/38331/how-to-change-default-launcher-icons-in-unity-for-a-new-user)

I am sure I can make something work from this.

---

### Post by collisionystm on 2013-02-11
Okay so it looks like the Guest Account has the ability to pull information from /etc/skel

So here is how you do the Unity Launcher icons and Wallpaper for the "Guest Session"

Make a temporary account.

Setup the Unity launcher how you wish. Choose what launchers you want on it..etc.

open a terminal

Switch to root privileges
```

sudo bash
```Create the missing directories in /etc/skel

```
mkdir /etc/skel/.config
``````
mkdir /etc/skel/.config/dconf/
```Copy the config 'user' file 

```
cp ~/.config/dconf/user /etc/skel/.config/dconf/
```So now the 'Guest Session' will have the exact unity launcher you just made.

The wallpaper will be the same ONLY if you chose a system default. 

Now you have 2 choices for the wallpaper situation.

Option #1, 
Put your custom wallpaper into the /usr/share/backgrounds folder
Select the wallpaper by doing the right click on the desktop, hit Change desktop background, and then proceeding with the above steps to copy the 'user' file.

Option #2

The location of your wall paper is in the following file

```
~/.gconf/desktop/gnome/background/%gconf.xml
```NOTE: ~/ is short for /home/YourUsername   - - - For those who didn't know.

You simply create the .gconf/desktop/gnome/background directories in /etc/skel and then create the appropriate %gconf.xml file

I suggest if you go with option 2, make sure you wallpaper file is in a directory accessible by everyone. Probably best to store it in /opt apply appropriate read/write permissions.


Hopefully this helped someone and maybe someone can write a program that does all of this for you. It would be nice to see a tool with a GUI in the software center.

---


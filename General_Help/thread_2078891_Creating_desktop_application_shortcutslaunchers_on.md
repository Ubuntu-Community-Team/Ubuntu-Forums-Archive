---
title: "Creating desktop application shortcuts/launchers on Ubuntu 12.04 or 12.10"
date: 2012-10-31
forum: General Help
---

### Post by wpshooter on 2012-10-31
At the following site it says "Right-click on the desktop background and choose: "Create Launcher.

[http://www.linuceum.com/Distros/osUnityCustom.php?srh=&hdr=o00000000000100](http://www.linuceum.com/Distros/osUnityCustom.php?srh=&hdr=o00000000000100)

But when I do that on Ubuntu 12.10, I do NOT see any line that says "Create Launcher".

Is there something I am missing on this ?

Thanks.

---

### Post by kanikilu on 2012-11-02
Just find the icon you want in the dash, and then drag-and-drop it to the desktop or launcher.

If you want to use that old familiar "create launcher" utility, you need to start it from the commandline: ```
gnome-desktop-item-edit Desktop --create-new
```

---

### Post by homin8or on 2012-12-31
When you start the application, it will appear on the launcher.  Right-click on the icon on the launcher and choose lock it to the launcher.

---

### Post by wpshooter on 2013-01-03
> **homin8or said:**
> When you start the application, it will appear on the launcher.  Right-click on the icon on the launcher and choose lock it to the launcher.

Perhaps I did not make my request clear.

I want the shortcut/launcher to be on the DESKTOP - not on that "Launcher" thing down the left side of the screen.

I want the programs/applications that I use to be in the place/location that I want them on the desktop and in the order that I want them placed on my desktop just like it always has been before and SHOULD be in the present and future.

Thanks.

---

### Post by fractaldg on 2013-01-04
> Perhaps I did not make my request clear.
> I want the shortcut/launcher to be on the DESKTOP - not on that "Launcher" ...

gnome-desktop-item-edit Desktop --create-new

The "Desktop" there is the name of the folder in which "--create-new" creates a new icon.
This command as listed assumes you are running it from your home directory (i.e. in a new terminal window).

Fractaldg

---

### Post by Inoki on 2013-01-06
Here is a solution: [https://apps.ubuntu.com/cat/applications/create-launcher/](https://apps.ubuntu.com/cat/applications/create-launcher/)

---

### Post by BCtom on 2013-02-23
Hi [[COLOR=#000000]wpshooter[/COLOR]]("http://ubuntuforums.org/member.php?u=41796"), I was also looking for the "right-click" option for creating short-cuts on my Desktop too. I had just done a re-installation of Ubuntu 12.04, so whatever I had added from the past that gave me my script to create a launcher was now lost. 

So, a sure fire way of getting that right-click on the Desktop option back is to install Ubuntu Tweak, and use it to add the script when you need to create a launcher.  Once you have added the script, it is there for the life of your current installation of Ubuntu. 

Go here for detailed instructions (See Option Number 4): [http://www.geekyboy.com/archives/384](http://www.geekyboy.com/archives/384)

Here's a thumbnail sketch of how to do it:

1. in Ubuntu Tweak, click the "Admins" tab
2. under personal, click Scripts
3. in the column on the Right, find "Creat Launcher" Then drag it over to the Left Column (under the nautilus-scripts folder
4. to test it out, find an empty spot, Right click on your Desktop and you should see an option in the menu (third down) that says "scripts" ==> Create Launcher.
5. create your launcher. 

I hope this helps.

---

### Post by paul_c2 on 2013-08-27
up

Just tried Ubuntu Tweak script, it doesn't work! :(

I found the script on the hard drive but didn't take the time to see if it was ok or not ... I'll take a look at it again tonight.

---


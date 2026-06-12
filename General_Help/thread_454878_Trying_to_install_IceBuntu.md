---
title: "Trying to install IceBuntu"
date: 2007-05-25
forum: General Help
---

### Post by merlinus on 2007-05-25
I downloaded icebuntu-default-feisty.tar.gz.  I open System/Preferences/Theme, select Install Theme and browse to the file, select it and then click Open 

I next get an error message that the file format is invaild.

Help appreciated.

Thanks!

-merlin

---

### Post by aysiu on 2007-05-25
IceBuntu is for IceWM, not Gnome.

If you're using System > Preferences > Themes, you're using Gnome and should use only GTK and Metacity themes.

---

### Post by merlinus on 2007-05-25
OK, and thanks.

What are the differences between IceWM and Gnome?  Can I give it a whirl and easily revert to Gnome?

When I tried KDM and wanted to go back to Gnome, it had trashed my installation and I had to start all over again.

Not a place I want to re-visit.....    :(

-merlin

---

### Post by aysiu on 2007-05-26
> **merlinus said:**
> 
What are the differences between IceWM and Gnome? IceWM is a lightweight window manager. Gnome is a full-blown desktop environment (using Metacity as its not-so-lightweight window manager).  > Can I give it a whirl and easily revert to Gnome? Sure. Read more [here](http://ubuntuforums.org/showthread.php?t=263710). > When I tried KDM and wanted to go back to Gnome, it had trashed my installation and I had to start all over again. KDE, you mean? I'm not sure what you mean about "thrash[ing]" your installation, but IceWM is fairly nonintrusive.

By the way, the IceBuntu theme just tries to make IceWM look like the default Gnome in Ubuntu.

---

### Post by merlinus on 2007-05-26
Thanks for the link.  I read through all the posts on that thread, and am about to give it a try, in hopes of expanding my knowledge and experience, and hopefully not trashing my Ubuntu linstallation, as happened when I test-drove KDE..

A few questions, though:

Is it better to use one of your two scripts (IceWM Script.tar.gz or icewm.tar.gz) to get IceWM, or use Synaptic? 

Which of the two scripts is preferable, or does it not matter?  Since I am using the default Gnome theme, I thought about trying Thin Black IceWM.

I did not learn, however, how to easily switch between Gnome and IceWM, once the latter is installed.  

I also missed how to easily logout from IceWM and then back into Gnome.

And in what file should I place the gnome-settings-daemon line?  (or something like that)

-merlin

---

### Post by aysiu on 2007-05-26
Don't use the scripts. I think they may be outdated. Not 100% sure, though.

For switching between desktop environments/window managers, check out [this page](http://psychocats.net/ubuntu/kde). It uses KDE as an example, but the principle applies to IceWM, too.

*gnome-settings-daemon* should go in /home/username/.icewm/startup and /home/username/.icewm/startup also has to be made executable first: ```
chmod +x ~/.icewm/startup
```

---

### Post by merlinus on 2007-05-26
Thanks again for all your wonderful assistance!

I tried using terminal to install icewm, but got this error message:

Couldn't find any package whose name or description matched "icewm-desktop"

So, do I need to use synaptic for this?

Also, although I know you prefer text-based configurations, it is useful to also install any of the gui-based managers for icewm?

-merlin

---

### Post by aysiu on 2007-05-26
There is no *icewm-desktop*. It's just *icewm*.

Do a search in Synaptic Package Manager for *icewm*, and you'll see *icewm* and all its related packages, including GUI config tools.

---

### Post by merlinus on 2007-05-26
OK.  I used synaptic to install the icewm packages.  But where are they located, and how do I start it?

I could not find .icewm folder in /home/merlin with show hidden files activated.  Is this something I have to create, along with the startup file?

Clearly I have missed something!

Thanks....

-merlin

---

### Post by aysiu on 2007-05-26
You start IceWM by logging out of Ubuntu and then selecting IceWM from the session options and logging back in again.

The ~/.icewm folder won't be created until you log into IceWM.

---

### Post by merlinus on 2007-05-26
I created a file named startup in .icewm, and made it executable:

#!/bin/sh
gnome-volume-manager &
gnome-settings-daemon &
lomoco &

But when in icewm, I do not see any of the GUI configuration tools, nor any programs besides a terminal, firefox, and gimp.

I read the help file, but probably am in way over my head.  I have no idea how to add my Gnome-installed  programs (e.g. bluefish, thunar, thunderbird, skype), add themes, change configurations, or anything else.

I can understand if you have had enough of me, and many thanks.  Perhaps I should stick to Gnome....

-merlin

---

### Post by aysiu on 2007-05-26
Well, let's be sure about what you're doing. 

*gnome-volume-manager* just makes sure that devices (iPods, cameras, USB sticks) that get plugged in are recognized and automounted.

*gnome-settings-daemon* allows you to have the GTK themes and looks of Gnome.

I don't know what *lomoco* is.

I believe if you want to add all the menu items for your installed programs, you install *menu-xdg* and *iceme*. If you want a GUI for configuring IceWM in general, install *iceconf*. I hope that helps.

---

### Post by merlinus on 2007-05-27
Thanks for hanging in there with me.

I tried to use icecm to get my apps into the IceWM menus, but nothing I did worked.  All I could do was enter the program name and executable file into a list, and then save it in a folder named apps in .icewm.

The iceconf app is also fairly useless.  And I could not figure out how to install other themes.

Never could get menu-xdg to load.

BTW, I used a terminal to load icecm and iceconf.

So I will read through the thread you began for IceWM again, in hopes of gleaning at least some useful info.  I think a good tip there is how to change the mouse-follow behavior.

-merlin

---


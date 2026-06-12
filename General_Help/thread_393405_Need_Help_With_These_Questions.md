---
title: "Need Help With These Questions"
date: 2007-03-25
forum: General Help
---

### Post by chobo2 on 2007-03-25
Hi

I am new to ubuntu(been using it for about a day now) I am using Edgy edition. I been a long time user of Windows and decided to start learning Linux since it is good to know.

So I have some questions.

**_Recycle Bin_** 

Right now my recycle bin is in my system tray bar but I would like to remove that and instead put that on my desktop.

**_Japanese Input_**

Right now I am learning Japanese and I would like to be able to write in Japanese. How I want it is like how it is Windows where I choose Japaneses(by using a hotkey) and then I would be able to write in Japanese and by hitting the hokey goes back to English.

**What I done so far:**

Went and installed Japanese language support
Searched Google and tried a couple things(none of them worked)

**_Hidden Windows_**

I am not sure what you call it so I just called it Hidden Windows but basically this is my problem. If I where on Windows and I would open up say Firefox. When Firefox would launch it would appear on the system tray area saying "Google Firefox" in a big tag but at least I would be able to know that it is open. 

However with ubuntu I don't know what I am running or not I can have 100 windows open and the only way I will know that something is running is if I use alt + tab to see what programs there are. 

So how can I fix this?

These are all my questions for now 

Added Questions:

**_How to install Themes,Icons from GNOME-Look.org?_**

I been looking at some themes and Icons but I can't find any tutorials or anything on actually how to install them I found some nice icons for firefox and some themes but once I download them I don't know what to do with them. I tried to go to themes but I did not know which I had to choose and all the ones I choose said it was invalid.

Thanks.

---

### Post by aysiu on 2007-03-26
**Trash on Desktop**
Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop > Trash should do it.

**Themes**
Download a GTK or Metacity theme and drag and drop it to the System > Preferences > Themes window. Do *not* extract the .tar.gz before dragging and dropping. Drag and drop it exactly as you downloaded it. Same should work for complete icon sets (not just Firefox icons).

---

### Post by rich.bradshaw on 2007-03-26
for the art stuff,

sudo apt-get install gnome-art

then

gnome-art

or find it in the menu, it's a gui to get things from the site. Works well.

---

### Post by AlexKarm on 2007-03-26
I'm sorry, I don't quite understand your problem with "Hidden Windows".

With the default setup (assuming you didn't accidentally remove it), open applications are shown the same way they are in Windows (in a bar along the bottom, each one represented by a single box on the "task bar", which in GNOME is called a panel).

Something that you wouldn't be aware of if switching to windows is the concept of multiple workspaces. Basically, you have a number of desktops availible to you (by default I think it's either 2 or 4). Right next to where the Trash icon normally is you will find some grey squares, with one highlighted (again, either 2 or 4). When you click on these, it will change your current "Workspace". Each workspace has it's own copy of the desktop, panels ("task bar"), etc. Each application is displayed only in it's own workspace. So, if you are in workspace 1, and you launch Firefox, and move to Workspace 2, Firefox won't be on the panel. It will be right where it was when you switch back to workspace 1 though.

This is actually a very handy feature, and there are Windows XP third party applications that allow for it in Windows, but they aren't nearly as efficient as the one that comes with Ubuntu.

Anyway, that may be what you are haveing trouble with. If it's not, please specify more.

---

### Post by chobo2 on 2007-03-26
> **AlexKarm said:**
> I'm sorry, I don't quite understand your problem with "Hidden Windows".

With the default setup (assuming you didn't accidentally remove it), open applications are shown the same way they are in Windows (in a bar along the bottom, each one represented by a single box on the "task bar", which in GNOME is called a panel).

Something that you wouldn't be aware of if switching to windows is the concept of multiple workspaces. Basically, you have a number of desktops availible to you (by default I think it's either 2 or 4). Right next to where the Trash icon normally is you will find some grey squares, with one highlighted (again, either 2 or 4). When you click on these, it will change your current "Workspace". Each workspace has it's own copy of the desktop, panels ("task bar"), etc. Each application is displayed only in it's own workspace. So, if you are in workspace 1, and you launch Firefox, and move to Workspace 2, Firefox won't be on the panel. It will be right where it was when you switch back to workspace 1 though.

This is actually a very handy feature, and there are Windows XP third party applications that allow for it in Windows, but they aren't nearly as efficient as the one that comes with Ubuntu.

Anyway, that may be what you are haveing trouble with. If it's not, please specify more.


I figured it out you had to add a window selector panel.

I am having trouble with installing Icons still:

I am using this theme: [http://www.gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548](http://www.gnome-look.org/content/show.php/MacOS-X+Aqua+Theme?content=13548)

The theme installed and is all good but I don't know if I installed the  icons right.

```
Step 3 : Move the entire folder named "MacOS-X" into ~/.icons

mv MacOS-X ~/.icons


I tried this however it did not work and got:

chobo2@chobo2-desktop:~$ mv MacOS-X ~/.icons
mv: cannot stat `MacOS-X': No such file or directory
```

I went to themes and then to icons and installed it from there so is that another way I can do it?

Also if you look at the themes picture if you look at the toolbar you see how it is like how do I get mine to be like that I applied the theme and icons but it still does not look like that.

Also I am having problems with my filesystem directory I can't seem to copy anything into that directory and I don't know why.

---


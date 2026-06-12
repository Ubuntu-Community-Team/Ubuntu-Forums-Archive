---
title: "Ubuntu 18.04 xrdp and admin gui issues"
date: 2019-02-05
forum: General Help
---

### Post by silverspr on 2019-02-05
Hello I am currently using a fresh install Ubuntu 18.04.1 with the minimal gnome desktop.  I have installed xRDP and it works well [COLOR=#ff0000]except [/COLOR]for admin privledges with gui style interface.  For instance using nautilus and "open as administrator" results in an empty window.  From a terminal: leafpad admin:///etc/apache2/apache2.conf also displays an empty window. I can edit a file directly using the terminal and sudo i.e. sudo nano /path/to/file but not through a gui interface.  I'm pretty sure this has something to do with the display window and xRDP...but not sure how to fix it.  I tried disabling Wayland, but that didn't make any difference. Using sudo nautilus . gives me: sys:1: PyGIWarning: Nautilus was imported without specifying a version first. Use gi.require_version('Nautilus', '3.0') before import to ensure that the right version gets loaded. But otherwise I am able to edit files as root.

admin gui empty window
[ATTACH=CONFIG]282406[/ATTACH]

sudo nautilus
[ATTACH=CONFIG]282407[/ATTACH]

Is there a better way to do this?
thanks for any and all help with this.

---

### Post by Claus7 on 2019-02-07
Hello,

1) could you try gksudo instead of sudo and see if the version problem disappears?
2) could you create a document in your Desktop folder and test it there? for example copy the apache2.conf file to your Desktop and then issue the command: gedit admin:///home/user_name/Desktop/apache2.conf

Usually when an empty file opens, it means that it does not exist and it is created at the time of issuing the command. 
Also, could you save the empty file in question in another place and see what you get? In other words open it the way you did that it showed like and empty file. Then write a couple of random words and save it to your Desktop. Then go to your Desktop and open it using gksudo: what are the contents of the file?

I do not use apache and xRDP, yet I tried it to one random file in my desktop with gedit and it was not a blank file - ubuntu 18.04.
I suppose so that you connect via xRDP to another computer and then you try to open the file in question: if this is the case, is it working in that computer while working directly with it? 

Just some thoughts.

Regards!

---

### Post by silverspr on 2019-02-08
hello, thanks for your help.  I used the apache2.conf file as an example: the file exists and is not empty. I tried other files as well which behaved in the same way.  I should elaborate, when I say empty, the admin window opens and never seems to load (spinning icon), so its not that the file is empty per se. I installed xrdp per this article: [https://c-nergy.be/blog/?p=12283](https://c-nergy.be/blog/?p=12283) not sure if that has any bearing.  This only happens using xrdp, if I work on the remote computer directly then the behavior is as expected, the file opens in an admin window.

---

### Post by Claus7 on 2019-02-10
Hello,

haven't tried this before, yet from the link you provided I was able to see that the people behind xrdp recognized some problems about gdm. Have you tried changing this in your system? What I mean is:
1) have you purged gdm and install lightdm and see any change?
2) have you tried installing the script with the fix they provide?
3) are you using xorg or something else in your system?

If  I were in your shoes I would try all these parameters and check which one is working. Just some ideas. You made it clear that xrdp cannot see the files in question and that these files are not empty.

Hope it will get fixed soon,
Regards!

---


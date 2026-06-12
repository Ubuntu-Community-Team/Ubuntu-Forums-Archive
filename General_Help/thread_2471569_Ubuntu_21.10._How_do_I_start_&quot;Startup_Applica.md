---
title: "Ubuntu 21.10. How do I start &quot;Startup Application Preferences&quot; with root?"
date: 2022-02-03
forum: General Help
---

### Post by Advait on 2022-02-03
Newbie here. How do I start "Startup Application Preferences" with root? The "/.local/" directory does not show up when I open this app and try to add an item.

---

### Post by KBar on 2022-02-03
Generally speaking, running GUI programs with elevated privileges is not recommended and not a good idea, to put it mildly.

Was */.local/* a typo and supposed to be *~/.local* instead? If so, then you don't have to be superuser to access files in your own home directory.

---

### Post by Impavidus on 2022-02-03
/.local/ doesn't exist on any normal Linux system. Maybe you meant ~/.local? That's owned by you (or at least, it should be), so you need no root permissions to access it. It is a hidden directory, like all files and directories starting with a dot, so not all tools show it without asking.

---

### Post by KBar on 2022-02-03
> **Impavidus said:**
> It is a hidden directory, like all files and directories starting with a dot, so not all tools show it without asking.

Thanks! I forgot to mention that part.

Advait, there should be an option to show hidden files in that dialog window. Try enabling that.

---

### Post by Advait on 2022-02-03
> **KBar said:**
> Thanks! I forgot to mention that part.

Advait, there should be an option to show hidden files in that dialog window. Try enabling that.

Nope, not there. But ctrl-h seems to work.

---

### Post by Advait on 2022-02-03
This image shows the details of the issue --> [https://imgur.com/eNtMaXo.png](https://imgur.com/eNtMaXo.png) After you review the image, please advise how to fix the problem.

---

### Post by KBar on 2022-02-03
Great screenshots. 

In Nautilus' window, whose home directory is it? Is there any other user besides *advait* (run [FONT=courier new]ls /home[/FONT] if you're not sure)? It's a bit weird that you have two different listings of the same directory, which leads me to believe they're actually located in two different filesystems.

---

### Post by Advait on 2022-02-03
> **KBar said:**
> Great screenshots.  In Nautilus' window, whose home directory is it? Is there any other user besides *advait* (run [FONT=courier new]ls /home[/FONT] if you're not sure)? It's a bit weird that you have two different listings of the same directory, which leads me to believe they're actually located in two different filesystems.

It's here --> [https://imgur.com/sPD9jze.png](https://imgur.com/sPD9jze.png) The next step?

---

### Post by Impavidus on 2022-02-03
That list of files looks completely different, as if it's a different directory. One is supposedly Home&#8594;.local&#8594;share&#8594;applications, the other advait['s home]&#8594;.local&#8594;share&#8594;applications. I'm using arrows instead of slashes because this is not the actual path. It looks like the GUI tries to be helpful by calling your home directory Home, instead of showing its actual name. But I'm on Xubuntu, so my GUI is different.

---

### Post by deadflowr on 2022-02-03
Startup Applications has nothing to do with the .local directory.
Those are in the ~/.config/autostart directory.

For root or system-wide startups those go in the /etc/xdg/autostart directory.
For only root user it would probably be the /root/.config/autostart directory. ( If that's even a thing)


I think different desktops like xfce or lxqt might have there own specific sub-directories somewhere, but i forget where, 
or even if those exist beyond my troubled mind.

---

### Post by KBar on 2022-02-03
> **Advait said:**
> It's here --> [https://imgur.com/sPD9jze.png](https://imgur.com/sPD9jze.png) The next step?

Peculiar indeed.

Select *Home* from that dialog window, click on the magnifying glass, copy the name of that Autostart_Rhythmbox file, paste it into the search field and let it finish.

---

### Post by deadflowr on 2022-02-03
Does adding a .desktop file as the command entry even work?
Don't you only want the specific command the desktop file runs?

---

### Post by schragge on 2022-02-03
Could it be that you started either Nautilus or **gnome-startup-applications** as root, and one of the screenshots shows **/root/.local/share/applications**?

---

### Post by Advait on 2022-02-03
> **deadflowr said:**
> Startup Applications has nothing to do with the .local directory.
Those are in the ~/.config/autostart directory.

In this thread [https://www.reddit.com/r/linuxquestions/comments/sinfou/how_get_rhythmbox_to_autostart_with_song/](https://www.reddit.com/r/linuxquestions/comments/sinfou/how_get_rhythmbox_to_autostart_with_song/) I was told to use the ~/.local directory for autostart files. Is this thread wrong? See the first post in this thread.

---

### Post by yetimon_64 on 2022-02-03
> **Advait said:**
> In this thread ...I was told to use the ~/.local directory for autostart files....

No you weren't told that; after creating the laucher (.desktop) file in the "~/.local/share/applications" and then altering the exec line you were then told to ...
> ...install GNOME tweaks, open it, go to the autostart tab and add Rhythmbox autostart. This next step, you seem to be missing, inserts rhythmbox into the necessary autostart location. There are 2 steps in your instructions, first is to create a custom desktop config file in ~/.local/share/applications, the second is in the above quote and is what will create you an autostart entry (in another location using gnome tweaks).

The instructions in that link appear to be OK to me. Though I must note I am not on Ubuntu and gnome but on Xubuntu and I don't even have rhythmbox or gnome tweaks installed here. Good luck, yeti.

---

### Post by Advait on 2022-02-05
It finally worked after I moved the .desktop file from one /.local directory to the other one. I tested it and Rbox is now auto-starting on boot with the correct song. Yay! Thanks for your help.

Still don't understand why I have 2 /.local directories but, well, that's Linux I guess.

---


---
title: "how to add a screen saver to ubuntu 24.4?"
date: 2024-07-07
forum: General Help
---

### Post by ronjjjg8885 on 2024-07-07
i've tried xscreensaver if i remember the name of it correctly but it didn't work. i've read that it won't work with wayland or something..

my question is how to add a screen saver? it should not lock the screen tho.

it is intended for my media center computer..

tnx

---

### Post by Dennis N on 2024-07-07
You're correct. xscreensaver does not work in a Wayland session. You will have to login to the "**Ubuntu on Xorg**" session at the login screen.

The xscreensaver packages you need:

xscreensaver
xscreensaver-data
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra

Another package with some of the best screensavers is **rss-glx**. But a couple of additional steps are needed to get these integrated into the xscreensaver system. Not difficult however, and worth it.

xscreensaver does not lock the screen unless you choose that option.

---

### Post by ronjjjg8885 on 2024-07-07
thank you very much..
the "Ubuntu on Xorg" needs to be chosen at each login? or will it be fixated when chosen once?

as for the packages. do i need to type "sudo apt get install xscreensaver".... and for all other packages with the same command or can i do it all with one command?

edit..
as for the xorg.. do i need to edit the '$ sudo nano /etc/gdm3/custom.conf' file for that like explained here?
[https://askubuntu.com/questions/1410256/how-do-i-use-the-x-window-manager-instead-of-wayland-on-ubuntu-22-04](https://askubuntu.com/questions/1410256/how-do-i-use-the-x-window-manager-instead-of-wayland-on-ubuntu-22-04)

---

### Post by Dennis N on 2024-07-07
> Does the "Ubuntu on Xorg" needs to be chosen at each login? or will it be fixated when chosen once?It stays fixed once chosen, until you deliberately switch back.
> as for the packages. do i need to type "sudo apt get install xscreensaver".... and for all other packages with the same command or can i do it all with one command?
You can install multiple items with one install command.
> my question is how to add a screen saver? it should not lock the screen tho.
'xscreensaver' will show up in your applications. Running it will open the settings dialog (see screenshot) where you choose the screensaver that appears and the time delay. The lock screen option is at the bottom - it's unchecked (off) by default.

You also need to add the command: ```
xscreensaver --no-splash
``` to your startup applications dialog so that it starts and runs in the background when you login to your session.

---

### Post by ronjjjg8885 on 2024-07-09
tnx
i've tried to find the way to switch to xorg but it is not like it used to be. i don't see the option in the login screen.
so how do i switch to xorg these days?

and please tell me how can i install all the xscreensaver packages at once? do i need to put a comma after each name of package?

can i choose that each time screensaver is activated it will randomly choose the screensaver from the list of screensavers?

edit..
i don't see the cog like explained here
[https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by ajgreeny on 2024-07-09
Just leave a space between each package name, not a comma nor any other punctuation mark.

---

### Post by Dennis N on 2024-07-09
At the login screen, while the password box is open, a little "gear icon" appears in lower right. Click on that to choose the "Ubuntu on xorg" session before submitting your password.

Using a random screensaver is one of the options in the "Mode" box (see the screenshot of post #4) of the settings dialog.

AJ Greeny answered the remaining question on installing multiple items.

---

### Post by ronjjjg8885 on 2024-07-11
thank you. i will try it now..

---

### Post by ronjjjg8885 on 2024-07-11
it is very small for some reason so i havent noticed before..
this is how it already was..
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293962&stc=1[/IMG]
is that means that i can use xscreensaver without any change?..

i will install the packages now..

edit..
ok. it is working with some crashes.....
how to integrate rss-glx into it?

tnx

edit..
i've found that explanation..

>     Run /usr/bin/rss-glx_install, which will look at your existing
~/.xscreensaver and add any missing entries. You probably want to back that
file up as the script is only lightly tested :)

but i don't know how to run the script..

edit..
i ran it as a program.....
is this screen shot shows that i've successfully installed rss-glx?[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293963&stc=1[/IMG]

i keep getting this..[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293964&stc=1[/IMG]

---

### Post by Dennis N on 2024-07-11
The warning is because you need to add xscreensaver to the startup applications - see command to add in post #4. Then restart, and choose the screensaver(s) you like and time setting. After this it should come on after your chosen time delay.

As to rss-glx, I never used the script to install them. I just copy the lines in file **/usr/doc/rss-glx/README.xscreensaver** after "Cut here" up to "End Here" and tnen paste those lines into ~/.xscreensaver right after where you see "programs". Save the file. 

Log out and Log in and the new screensavers should appear in the settings list.

---

### Post by ronjjjg8885 on 2024-07-24
thank you

---


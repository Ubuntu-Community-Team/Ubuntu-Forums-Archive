---
title: "Unable to log in to 12.04, Log In loop. Guest session still working"
date: 2013-03-29
forum: General Help
---

### Post by KittyCatHerder on 2013-03-29
I have just tried to restart my machine and when the log on screen appeared and I attempted to log in to a Gnome Classic session, my password was accepted, and I saw some flashing /shell/text lookign stuff, and I was returned to the log in screen. Just before this I got some updates through the update manager, and I was also editing my global keybindings file form the gconf-editor. The only thing I remember changing was binding "command 1" to Super_L and assigning gnome-terminal to command 1. The guest session still works normally but I have no idea how to repair my regular user so that I can use Ubuntu normally.

I have an Acer netbook with pretty standard hardware and software. I use GRUB 2 and still have a copy of Windows 7 installed in case of situations like this when I can not use Ubuntu.

Is this common? Does anyone know how to go about repairing this? 

Edit 3/29/2013 -- I have found forum posts made by several other Ubuntu 12.04 and 12.10 users that have had the same problem. The consenus, as far as I can tell, is that the problem is probably either caused by a problem with the Xauthority file in ~, used by the Xorg/X server or it is caused by 'lightdm' of which I have no knowledge. At least one eprson had success in fixing the problem by 1) cd to /home/(your user name), 2)Run the command mv Xauthority Xauthority.bak, 3) reboot, which did not work for me. Another process that has worked for other people -- 1) Drop to root shell by pressing Ctrl + Alt + F1, 2) Run command sudo apt-get install --reinstall xorg, 3) reboot, which also did not work for me.

I don't know what else to do. I would love some help!

Edit 2 -- 3/29/2013 -- I found the solution! It turns out the problem was with the .Xauthority file in /home/user. I don' tknow exactly what the problem was with the file but droping to root shell by pressing Ctrl + Alt + F1 and removing the .Xauthority file by typing rm ~/.Xauthority, rebooting, and typing sudo apt-get install --reinstall Xorg. I Experienced the strange condition of only have two work spaces on my desktop after the first reboot but another reboot fixed that.

---

### Post by 3rdalbum on 2013-03-29
Here's where the words "which didn't work for me" are not very helpful. If you'd said something like:

> mv Xauthority Xauthority.bak didn't work, it gave me an error message "No such file or directory"

then someone would have quickly pointed out that it should be .Xauthority as that's the name of the file (it's hidden because of the dot in front of the name), and you probably need to run the command as root, like so:

```
sudo mv .Xauthority .Xauthority.bak
```

Also, for people coming along later looking for solutions, you don't need to reinstall Xorg after that.

The .Xauthority file sometimes becomes root-owned by accident if you use 'sudo' to run graphical programs. If you are running a terminal command as root, use sudo. If you are running a GUI program as root, use gksudo instead. For Compizconfig Settings Manager, you shouldn't run it as root at all.

I'm glad you got your problem sorted out anyway. Congrats!

---

### Post by KittyCatHerder on 2013-03-29
> **3rdalbum said:**
> Here's where the words "which didn't work for me" are not very helpful. If you'd said something like:



then someone would have quickly pointed out that it should be .Xauthority as that's the name of the file (it's hidden because of the dot in front of the name), and you probably need to run the command as root, like so:

```
sudo mv .Xauthority .Xauthority.bak
```

Also, for people coming along later looking for solutions, you don't need to reinstall Xorg after that.

The .Xauthority file sometimes becomes root-owned by accident if you use 'sudo' to run graphical programs. If you are running a terminal command as root, use sudo. If you are running a GUI program as root, use gksudo instead. For Compizconfig Settings Manager, you shouldn't run it as root at all.

I'm glad you got your problem sorted out anyway. Congrats!

I posted that edit in restrospect and I did well to remember what I did. The file names I used, .Xauthority and .Xauthority.bak were correct when I ran them, I just forgot to put those .'s in front of the file names when I recounted later. That action didn't work. I had to remove the .Xauthority file. I read in several places that a similar condition was apparentely caused by updates. 

Maybe this was caused by updates and not by running a graphical program as root? I don't remember runningg any graphical programs as root within the last couple of days. 

What is Compizconfig Settings Manager and how come I shouldn't run it as root?

---


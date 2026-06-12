---
title: "Log into a blank tan desktop"
date: 2008-02-08
forum: General Help
---

### Post by jeffsa12 on 2008-02-08
I have been using Ubuntu 7.10 regularly for the last month or so. All has been well until I switched to pulse audio packages using synaptic from the repositories. I removed the ESD package same time as adding the pulse packages. I got an error pop up box...something about network....before synaptic finished with the install. After the files were loaded and synaptic updated, things were not right with my main menu, missing apps, etc, so I rebooted. Ktorrent was uploading files in the background when this happened and not sure if this was a problem. I also have several deb packages installed that were not in the Ubuntu repositories, but as I said, everything has been running smooth until this last change. The non repository deb packages I have loaded are, a stand alone version of Krita, Nero linux, Acetone ISO, flash 9.0.115, grub editor, xorg-edit, Ubuntu tweak.

This is a detailed list of the symptoms.

Start up computer
Boots into acronis OS detector
Select Linux OS....Ubuntu 7.10 in this case
Loads grub boot loader
Select Ubuntu kernal2.6---etc--etc
Loads Ubuntu log in screen
Log in
Loads to a blank tan screen.

Tan is not my desktop wallpaper colour. It's not the default wavy dark brown wallpaper either. The mouse cursor moves around, but no other mouse or keyboard input has any effect except the ctrl+alt+backspace kills X normally, returning to the log in screen.

I have on board ATI 200 express graphics in this one and use the fglrx ATI driver. It seems as though the problem may not be X related but not really sure....I have always had a dark, blank screen or a visible screen with 600x800 resolution setting when X settings or the driver has had problems.

Searching for a solution, I found the following, but I'm not sure it applies, and not sure how to fix it if it is this problem.

[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/175682/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/175682/+viewstatus)

---

### Post by darvasi on 2008-02-09
Hi,
It seems that your xorg.conf has been smashed a bit.
try the next ONLY
If you can load the ubuntu live cd with no problems, so everything is fine.
1. Load ubuntu live cd
2, Click 'places' - 'computer'
3. Open - filesystem -etc - X11 directories
4. Double click 'xorg.conf' it will be opend in a text editor
these options are the ubuntu live cd's VGA settings. (resolution, your monitor, color etc)
5. press 'ctrl+a' (means select everything from the actual screen)
6. press 'ctrl+v' (copy everything...)
7. close the window click x on top right.. :)
8. Go again 'places' - 'Computer'
9. Double click on your drive which says 47.3GB VOLUME (it's my linux hdd size yours has got different numbers) If you have windows too make sure that you click on that hdd which has got the LINUX files!!!
With this you have mounted your original linux hdd and we can configure it now.

Now we need to rewrite your originaly installed VGA settings.
1. click to 'Applications' - 'Accessories' - 'Terminal'
it will open a terminal application
2. type in the terminal window the followings (at the end of each line you need to press enter) :
 
cd /media/disk
cd etc
cd X11
sudo gedit xorg.conf

Now you should see your originaly installed VGA setting in a text editor.

3. press 'ctrl+a'
4. press 'delete'
5. press 'ctrl+v'  (it will copy your ubuntu live cd's VGA settings to your original VGA conf)
6. click on the SAVE button at the top of the editor.
7. close it down - click x
8. Restart your computer (now you should get back your original screen)

Hope it helps
Let me know 
AD

---

### Post by gayle_raglan on 2008-02-11
I'm having the exact same problem, although the blank tan desktop is EVERY time I try to log in.
Therefore, it's impossible for me to try this out as I cannot open "places", drives or anything.
The only thing I have managed to do is launch "Screen Shot" by pressing the print screen button on the keyboard. from there I can open Help and then launch Forefox by cicking one of the links there.
That's how I got onto the forum here to plead for help?:confused:

---

### Post by darvasi on 2008-02-13
Hi,

Do you have this problem when you log on to the ubuntu live cd?
I means actualy you don't start the installed ubuntu just put the live
cd in and start the computer and let it to boot from the live cd.
If that works fine you should follow my instructions above.
I mean do everything with the live system booted 
and not the system on your hard disk.
Let me know.

---

### Post by jeffsa12 on 2008-02-14
Hey Thanks darvasi.....

I had tried changing to a couple different xorg.conf files before I posted here. I have  learned from previous linux installs....and problems with my ATI on board graphice and the fglrx driver to **backup** good xorg files** as soon as I get X working well.** I used my Mint install on the same computer to replace it with a known good backup from Ubuntu and the backup for Mint and that changed nothing. I did follow your suggestion and also copied and tried the one from the live cd while running.....also no change.

I also tried deleting all the folders w/ files from Ubuntu root that had "gnome" in the name, replacing them with the ones from Mint that were working fine. No change.

In the end, however, I did solve the problem by reloading Ubuntu onto my hdb7 root partition. That worked out well and I saved all my changes to my Ubuntu desktop by leaving it's home partition intact. All I had to do is reload a few deb packages that I had saved in a seperate partition, and I was off and running. I also got Mint set up to pretty much duplicate my Ubantu install.......so now I have a quick option if need be. 

I'm not sure if my problem was the same as the bug link in my first post.....and I didn't figure out if and how to try a fix based on that info anyway.. The reload fix is really slick with linux compared to a reload of win.

I am finally a full time, converted linux UBUNTU / MINT user at this point. 

I also want to give a HUGE THANKS to all the Linux programmers, software developers, the people who support Linux distros "Ubuntu" and others and the distro communities for their  support and documention.  Thanks for making Linux a simple and pleasant enough OS for a regular "no tech guy (me)" to use.

---


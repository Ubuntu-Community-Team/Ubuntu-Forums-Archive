---
title: "Problem with GNOME ?"
date: 2007-07-19
forum: General Help
---

### Post by md_lasalle on 2007-07-19
Hi all, I'm using uBuntu 6.10.

After a normal shutdown, I rebooted my ubuntu OS and had problem after login in

this is the message that appeared :

[INDENT]There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.[/INDENT]


Now, if I'm patient, I get to the OS, everything looks normal, except that if I try to boot anything ( like terminal ) it shows in the bar that I'm starting Terminal but it never shows up and disapears from the bar

If i restart my computer a few times, i can get it to work.

One thing i noticed, normally the Terminal prompt would look like that :

marcd@laptop-marc:~$

and right now, it looks like this :

marcd@(none):~$

Could my computer have lost it's name ???

because of this, when i hit NumLock or CapsLock on the keyboard, I get this message :

[INDENT]An error occurred while loading or saving configuration information for gnome-settings-daemon. Some of your configuration settings may not work properly.

Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-(none)/0/numlock_on": `(' is an invalid character in key/directory names[/INDENT]


Thanks for any help, this is my main game development OS and it's getting a pain to have to pray everytime I boot uBuntu :(

---

### Post by Happy_Man on 2007-07-19
From what I can tell, you've done something to completely screw up the GNOME backend. The only thing I can suggest for you is to reinstall..... sorry. The laptop losing its name is big. I dunno what that is a result of, but if it has happened, something big's gone bad.

---

### Post by md_lasalle on 2007-07-19
thanks for the answer

could i just reinstall GNOME, or i have to reinstall my OS aswell ?

---

### Post by Happy_Man on 2007-07-19
> **md_lasalle said:**
> thanks for the answer

could i just reinstall GNOME, or i have to reinstall my OS aswell ?
I dunno. Try reinstalling GNOME first, and if that doesn't work, reinstall the OS.

---

### Post by md_lasalle on 2007-07-21
allright, booting into KDE and reinstalling gnome with the synaptic package manager fixed it.

as for the hostname, i edited the file called /etc/hostname, just wrote my hostname there and i have my hostname back after a reboot!

---

### Post by beerorkid on 2007-08-03
when you say reinstall gnome what packages did you reinstall?

My wife is having this issue at work and I had her install KDE and then reinstall ubuntu-desktop but it did not help.

---

### Post by swiftstealth on 2007-08-03
hey, I've got the same problem, but I'm a total noob, so if someone could please post a how to reinstall gnome walkthrough thatd be great..

well not totally the same actually. my computer still has it's name and num lock works fine. other then that exactly the same with the OS taking forever to boot up. would reinstalling gnome fix it?

---

### Post by newagelink on 2007-08-03
[COLOR="DarkSlateBlue"]What sorts of things can do you do cause this error?[/COLOR] :-#

---

### Post by swiftstealth on 2007-08-03
I only changed 3 things and I got this error message. I changed my theme, altered a keyboard shortcut, and tried to change the sound that is played when you boot up the computer(the default sounds annoyed me) anyway I changed it and then after I made the changes I rebooted and got the error message :( :confused:

---

### Post by wersdaluv on 2007-08-04
Are you from De La Salle University?

Sorry for asking. Your user name made me curious. :D

---

### Post by fusionisthefuture on 2007-08-18
im also having this problem, it sounds just like the OPs problem, but my numlock does work, and so does terminal, but some of my networking stuff doesnt, like mediatomb, and i cant access the administrative network application.  

does anyone have any way to troubleshoot this to see exactly what the problem is?  
thanks in advance
-arne

[IMG]http://img242.imageshack.us/img242/7638/screenshotgnomesessionjn9.png[/IMG]

---

### Post by beerorkid on 2007-08-18
well I am not exactly sure how my wife fixed it, but I had her reinstall gnome, ubuntu-desktop, and a few other things like deleting .gnome2.  She restarted X a few times and it did not fix it.  Eventually she did a full reboot and the problems went away.

---


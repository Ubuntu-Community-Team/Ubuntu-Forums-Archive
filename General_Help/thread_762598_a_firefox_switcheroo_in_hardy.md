---
title: "a firefox switcheroo in hardy"
date: 2008-04-22
forum: General Help
---

### Post by tich on 2008-04-22
when most people start firefox they click on the shortcut in their menu and ubuntu finds a file called firefox in this folder:
/usr/lib/firefox-3.0b5
and then the magic of using firefox begins.

when i try to open firefox using the menu nothing happens, and when i try alt-f2 an error window pops up with this:
Could not open location 'file:///home/tich/firefox'
The location or file could not be found.

it is obviously looking in the wrong spot.

although i am now using hardy heron i first tried firefox3 with gutsy and i remember having to do some fancy footwork (aka copy and pasting) to get it to work and to get it to work in the menu.
i might have used one of these howto's:

[http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html)

[http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710](http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710)

[http://www.alterego7.com/2008/03/firefox-3-beta-3-on-ubuntu-710-gutsy.html](http://www.alterego7.com/2008/03/firefox-3-beta-3-on-ubuntu-710-gutsy.html)

but it was a really long time ago and i don't remember which howto i used (to be perfectly frank i don't even remember if it was one of the 3 i listed).
what i want to do now is have ubuntu find firefox in the right location and start it when i click on it in the menu.  how would i redirect the link to the appropriate file in the appropriate folder?

oh yeah, if i actually go to /usr/lib/firefox-3.0b5/ and choose the firefox file it will open the browser so it is all there and it is all working.  it just can't be found.

---

### Post by NewDisciple on 2008-04-22
Check system-preferences-preferred applications-internet.  What is listed in the
command line?  Should be path to Firefox.  If it is not correct then change it.

---

### Post by tich on 2008-04-22
thanks for the suggestion.  i tried it and firefox still doesn't work.  
the preferred applications might only affect the settings for default apps rather than the path to the apps.

but it was definately worth a shot.

---

### Post by jen1963 on 2008-04-22
Open the menu editor then right click on the Firefox entry and select properties. Under Properties -->> Command make sure the line in Command points to the Firefix executable in /usr/lib/firefox-3.0b5/
You may have to adjust the properties of any links on your taskbar as well.

---

### Post by tich on 2008-04-23
b@b-laptop:/usr/lib/firefox-3.0b5$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
b@b-laptop:/usr/lib/firefox-3.0b5$ sudo apt-get install firefox-3.0
Password or swipe finger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
firefox-3.0 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

today i tried to run it from the directory it is installed and i received the above weirdness.
what does it mean that firefox-3.0 is set to manual install?

i am about to try the suggestion in the above post but after recieving this terminal output i am doubtful...
i will post if it is successful and if it isnt!

---

### Post by tich on 2008-04-23
unfortunately editing the paths in the menu editor didn't fix it.
thanks for the idea though.

upon further testing (aka trial and error + bumbling) i have discovered that it is only possible to run it using sudo nautilus and choosing the file (regular nautilus has no effect and using a terminal and typing sudo firefox from the usr/lib/firefox-3 directory doesn't even do it).

i can't imagine why this would it would behave like this... maybe it has something to do with firefox-3.0 being set to "manual install" (refer to above post)

i guess at this point i would be happy to go one of two ways:
1. fix this weirdness and reconnect the paths and fix permissions

2. completely purge firefox (including these odd settings-- apt-get purge doesn't do it, i have already tried) then reinstall firefox

if anyone their are any other suggestions (for either option) i will happily try them.

thanks.

---


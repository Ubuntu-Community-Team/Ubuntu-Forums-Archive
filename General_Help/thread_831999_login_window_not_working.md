---
title: "login window not working"
date: 2008-06-17
forum: General Help
---

### Post by jordanh06 on 2008-06-17
okayy.... im pritty new to linux and ubuntu but i tryed to chasnge the splash screen(wish i hadn't) and the gdm log in window. The splash screen loads the normal ubuntu screen byt when it comes to the login it just loads and does not want to stop.

please help, im having to use stupid windows :(

---

### Post by manfer on 2008-06-17
I understand gdm loads but you don't see the text field to enter username and password or anything else.

Try if you can enter a terminal by pressing the keys Ctrl+Alt+F1

*F1 is the function key on top of keyboard (F1, F2, F3, F4...)*

If it works identify yourself as root. Username:root password:yourRootPassword

Now test if you have connection to Internet with ping command:

**<root>#** ping -c 2 [www.google.com](www.google.com)

If that command show you 2 packets transmitted, 2 received, 0% packet loss, then the connection to internet is working and you can go on.

Now you are going to reinstall gdm.

**<root>#** apt-get purge gdm

**<root>#** dpkg --configure -a

**<root>#** apt-get install gdm

**<root>#** apt-get install ubuntu-desktop

**<root>#** reboot

Gdm should work with its default human theme after the reboot of system.

If you can't enter the terminal that way (Ctrl+Alt+F1 from gdm) try entering the terminal from grub menu. You have to choose from the menu the recovery mode. It would show you a menu where you have to choose root. Then you are at a terminal where you have to enter your root password and you can do the rest: testing if you have internet connection with ping and reinstalling gdm with the commands I mentioned before.

Don't do anything if the ping test reports not working Internet connection (100% packets loss), you don't want to uninstall gdm if you can't install it again.

---

### Post by beckols on 2008-06-17
The last time I purged and reinstalled ubuntu-desktop, it messed up a bunch of things.  This probably wasn't the norm, but just in case before you try that, try changing your theme back to default.  I'm assuming it was just the theme that you changed right?

first log in to another terminal (like guy above said ctrl-alt-f2)

use your editor of choice to edit the gdm.conf file, I'm using vi:

sudo vi /etc/gdm/gdm.conf

then search for "GraphicalTheme" (to search in vi: while in command mode (press esc to make sure) type this: "/GraphicalTheme" press n to go to next instance of it until you get to a line that looks like this:

GraphicalTheme=<your other theme>

change this to:

GraphicalTheme=Human

then save and quit (in vi type ":wq" in command mode)

now press ctrl-alt-backspace

if it worked, the original ubuntu login screen should now pop up

---


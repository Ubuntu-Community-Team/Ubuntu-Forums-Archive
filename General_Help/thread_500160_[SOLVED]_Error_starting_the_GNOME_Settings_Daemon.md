---
title: "[SOLVED] Error starting the GNOME Settings Daemon?"
date: 2007-07-13
forum: General Help
---

### Post by rainwalker on 2007-07-13
Background Info:
I'm running Edgy on an Inspiron 8600, upgraded from Dapper.
With this computer, it sometimes thinks that it was turned off because it overheated. I've found that it only thinks this if you shut it down while the fan is running. 
If this happens, the next time the computer is turned on it will say that it turned off because it overheated and to F1 to boot normally. 
This really isn't a problem, but today I accidentally pressed Esc right after F1 (they're right next to each other) and was taken to the boot menu. I honestly don't know which kernel I use, but since there's only two different versions I know that one is the Dapper kernel and one is the Edgy kernel. So, I booted the first one in the list (2.6.15-27-386, the Edgy kernel) in normal (not recovery) mode, and it seemed to load fine. I got to my login screen and logged in, and that's where the problems start.
Instead of the Ubuntu splash screen showing and my desktop loading, it leaves me with a blank screen (that light brown Ubuntu color) and my mouse, nothing else. After a few seconds, a gray box appears in the upper left hand corner. If I give it a little more time, my desktop eventually loads and that gray box turns out to be an alert window, it says this:
> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the settings Daemon next time you log in.
Looking at my screen, I see that all icons are the standard GNOME ones, rather than the pretty Human-theme ones. Oddly enough, though, if I go to Sytsem -> Preferences -> Theme and select something, like re-selecting Human as the theme for the controls, everything will change correctly.
The sounds all play correctly, and my desktop wallpaper does load.

I tried shutting down completely and turning it back on and logging in again, and the same thing happens.

I'm really inexperienced with all this (I'm 15 and still learning the ropes), so I didn't want to try booting into recovery mode because I don't know what it is.
I did try the old (Dapper) kernel, and it doesn't work. It will load the essential drivers, and then get stuck trying to load the root file system and then take me to some kind of command-line interface.

Has anyone else had this problem? Better yet, does anyone have any idea how to fix it?
If it helps, the only updates I installed yesterday were ones for OpenOffice.

---

### Post by rainwalker on 2007-07-13
I'm not sure if this has anything to do with it, but being the stupid person I am, I decided to get rid of the "auto lo" line in my /etc/network/interfaces file, and I think that was important. Now, if I try to use a terminal to do "sudo gedit /etc/network/interfaces" and enter the password it never opens, but it does if I get rid of the "sudo".

---

### Post by rainwalker on 2007-07-13
Okay, so I want to try using the command line to edit my interfaces file, but in a non-GUI-dependent way. My plan is to use whatever the shortcut is to go from the login screen to a command-line interface and use VI to edit the file, because it doesn't want to work when used with a GUI.
But...does anyone know the shortcut to change from a normal login screen to a command line-based one?

---

### Post by rainwalker on 2007-07-13
That fixed it!
Apparently the "auto lo" thing is essential in the interfaces file.

For anyone who might need it, this is what I did:
From the login screen, Ctrl + Alt + F1 to go to a command line-based login
Edited my interfaces file with VI, added "auto lo" back into it
If you use VI, you have to press Escape to be able to enter commands, and type "ZZ" to save the file
I used the "shutdown" command, but I guess you don't have to

And now it all works!

---

### Post by RedKyuubi on 2007-07-16
I have the same problem, do you possible have a solution for those who still have a working auto lo file?

---

### Post by src04c on 2007-08-07
for me it was the internet password and other keyrings in the keyring manager, i just deleted them and i was all better! Reset them the next time i reboot and logged in.

---


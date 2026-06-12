---
title: "Almost toatally restrict a particular user - only to play games"
date: 2006-12-21
forum: General Help
---

### Post by Portable_Jim on 2006-12-21
I understand that only programs run as root can change system settings.

I am going to set up a number of PCs to be games only PCs - by games I mean Linux games such as frozen bubble, nibbles, etc. The computers are going to be available for many people to use. Because of this, I was wondering whether there would be a way to restrict a user's access to chance settings. (including the ability to alter the panels, change anything in System --> Preferences, changing the background, or anything else  to 'personalise'   the account.) 

However, they still will need to have access to the games that are on the machine.

The computers will not have access to the internet.

I am planning to put dapper on the machines.

---

### Post by dbw on 2006-12-21
What if you use a Windows manager like Fluxbox or enlightenment?  Then you can completely restrict the menu to only include games and a log-off.  If you make the settings files all owned by root, the users will not be able to change them.

---

### Post by Portable_Jim on 2006-12-21
found:
[http://www.ubuntuforums.org/showthread.php?t=307052](http://www.ubuntuforums.org/showthread.php?t=307052)
could it be the answer?

---

### Post by Portable_Jim on 2006-12-21
(bump)

---

### Post by dbw on 2006-12-22
Jim - 
  Try using Enlightenment Window manager.  Not only is it pretty, the menu files are controlled by text files in the user's home directory.  If you choose, you can limit what applications appear on these menus.  If you remove menu-editing apps, and the terminal, they will not be able to change their menus.  If you then chown root all menu and configuration files, the users will not be allowed to edit their settings, but should still be able to save games in their home directories.

---

### Post by Portable_Jim on 2006-12-24
> **dbw said:**
> Jim - 
  Try using Enlightenment Window manager.  Not only is it pretty, the menu files are controlled by text files in the user's home directory.  If you choose, you can limit what applications appear on these menus.  If you remove menu-editing apps, and the terminal, they will not be able to change their menus.  If you then chown root all menu and configuration files, the users will not be allowed to edit their settings, but should still be able to save games in their home directories.
I'll try that.

---

### Post by Portable_Jim on 2007-01-19
> **dbw said:**
> Jim - 
  Try using Enlightenment Window manager.  Not only is it pretty, the menu files are controlled by text files in the user's home directory.  If you choose, you can limit what applications appear on these menus.  If you remove menu-editing apps, and the terminal, they will not be able to change their menus.  If you then chown root all menu and configuration files, the users will not be allowed to edit their settings, but should still be able to save games in their home directories.

is it a light window manager??

I want to set it up on 400Mhz computer with 128 - 256 MB RAM.

---


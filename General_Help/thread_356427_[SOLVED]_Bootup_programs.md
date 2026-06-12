---
title: "[SOLVED] Bootup programs"
date: 2007-02-08
forum: General Help
---

### Post by tbrminsanity on 2007-02-08
I'm having troubles trying to add programs to the list of programs that auto load when the desktop loads up.  The main programs that I want to load are my firewall and support for my extra buttons on my mouse and keyboard.  I have tried adding them in on the sessions configure menu but that does nothing.  Is there some file somewhere that I need to modify?  Help please!

---

### Post by DagMan on 2007-02-08
If you're using the firestarter firewall, then it's rules are loading on boot automatically.  You only need the GUI to change rules and have the conveniance of looking at the log it puts there and what you're connected to.  If you want to start the GUI at boot anyway, have a look here:
[http://ubuntuforums.org/showthread.php?t=26483&highlight=sudo+visudo+firestarter](http://ubuntuforums.org/showthread.php?t=26483&highlight=sudo+visudo+firestarter)
However if it's starting with the gui and needs minimising, do this for the last step:
sudo firestarter --start-hidden
and note that sudo must be used instead of gksudo to start it hidden

What are you using for the mouse and keyboard shortcuts?
If it is xbindkeys, do you have xbindkeys loading at boot and if so (or whatever you're using actually), was it in a script and was placed directly after the firewall entry that the firewall might not have executed (lacking root priveleges) and the script never made it to the keyboard and mouse bindings?  If you had them both as separate entries in sessions then this wouldn't be the case but if you have one script in sessions that does all your startup stuff it's worth looking at.

---

### Post by tbrminsanity on 2007-02-09
That didn't work.

There is something wrong with my "System->Preferences->Sessions".
It won't accept any new values for Boot up programs.

---

### Post by DagMan on 2007-02-09
Try checking the permissions and ownership of the files in /home/username/.config/autostart and of that folder itself.

My permssions are 700, and owner is me, for both the directory and the file inside that corresponds to what I've added.

---

### Post by tbrminsanity on 2007-02-10
That worked like a charm.  Autostart was set to root.

---


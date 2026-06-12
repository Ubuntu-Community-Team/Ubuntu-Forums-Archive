---
title: "Empty Applications Menu: Here's a Fix"
date: 2007-09-02
forum: General Help
---

### Post by wyth on 2007-09-02
Recently after a KDE to Gnome conversion, I lost my applications in the Applications menu.  I'd click on it, and would see nothing except a small pixel on the bottom-left corner below "Applications" -- no menu, no apps.  I tried to edit the menu, but alacarte just spun its wheels and then stopped.  I did the regular searches -- google, ubuntuforums, linuxquestions.org, launchpad, all to no avail.  Every answer was overly complicated (a bug with gamin/installing missing applications/create a new user), and none seemed to hit the mark.

Here's the fix:

In /home/user_name/.config/menus, there's a file called "applications.menu." If you get an empty Applications section of the Main Menu app, that's because somehow this file was emptied.  If you open it, it's blank. 
 
So check in /etc/xdg/menus for another file called "applications.menu." That file should have plenty of info, and it may have information from previous edits (meaning after the fix, you may have to re-edit your menu). Either copy that file into /home/user_name/.config/menus, overwriting the applications.menu file that's already in there, *or* copy the text into the applications.menu file in your /home/user_name/.config/menus directory.  

This should work.  At least it worked for me.  I rebooted to make sure it stuck before I decided to post this.  Yep, the fix stuck.  My menu's back.  I hope your's is too.

---

### Post by Esther on 2007-09-23
I am having the same problem, but if I go to home/esther (my username) I cannot find any file named applications.menu.

I am completely new to Ubuntu and it was not my choice to have it on my computer (though I really like the interface and the way it works), I really don't have the time to get into this. I knew quite something about windows and how to fix problems. Unfortunately my computer wouldn't install windows any more, no idea why and a friend of mine installed Ubuntu. I used to have the applications menu, but now it is completely gone.....How to fix this??


*Okay, I have found the solution! My computer wasn't showing hidden files......how dumb of me. But I got my applications menu back! :-)*

---

### Post by wyth on 2007-09-25
Hi Esther,

First, if you're using Gnome, once you're in your home folder, do a ctrl-h.  That will show the hidden files (and this is a hidden file).

Then look for the .config folder.  

Inside that is a folder called menus.

Inside that is the applications.menu file.

Hope that helps some.

---


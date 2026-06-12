---
title: "MAIN MENU problem!"
date: 2007-08-23
forum: General Help
---

### Post by sdim on 2007-08-23
Dear friends,

I've been using Ubuntu for 10 days now.Up to now,there were no problems,but 
during the past half hour,I've been experiencing a strange problem.
The problem is this:
First of all,I must have clicked on something (or done something I didn't 
realise) and made the applications disappear from the start bar.I could only 
see the Ubuntu icon,but there were only 2 things in there (systam,places and 
EXIT),so  removed them and I right-clicked on the panel,and added TOOLBAR MENU.
Now there are three things on the bar:APPLICATIONS(with the Ubuntu icon next 
to it),PLACES and SYSTEM.
When clicking on the SYSTEM word,I get HELP AND SUPPORT,ABOUT UBUNTU and ABOUT 
GNOME.
Clicking on the PLACES word,I get the usual catalog,but when I click on the 
APPLICATIONS word,I get absolutely nothing!
Even right-clicking on it,does nothing!
  I did right-click on the Ubuntu icon and selected EDIT MENU,then it says at 
the bottom"starting menu" but it goes out after 10 seconds.Nothing happens...

I would appreciate any help,as I can't open any of my programs or utilities.If 
nothing can be done,is there a way I can reload the default start menu? 

P.S. When right-clicking on APPLICATIONS-->EDIT MENU,the Firefox icon shines 
up,but nothing happens.Does this have anything to do with it?

Many thanks in advance

---

### Post by gashcrumb on 2007-08-23
That's definitely weird, I haven't seen that one.

Two things to try, first is try adding the "Main Menu" widget and see if that works any better.  The "Main Menu" is a single icon that contains the Applications, Places and System menus.

Other option is try logging out and logging back in.  If your System menu doesn't have "Log Off..." (it should BTW) you can hit Ctrl-Alt-Backspace to restart the X server, then you can log in again...

---

### Post by sdim on 2007-08-23
I think I must have hit a combination of CTRL+ALT+F1 keys at some point(don't remember why exactly,though),and ended up at a black screen telling me to write username and password,which I did, and I ended up here.
Anything to do with that,maybe?

Attached a screenshot of *gnome application info* file (don't know if it helps).

---

### Post by gashcrumb on 2007-08-23
That shouldn't have hurt anything, Ctrl-Alt-F1 takes you to a text console, one of 6 that are available via Ctrl-Alt-F1 thorugh F6.  You can get back to X/gnome by hitting Ctrl-Alt-F7.

As an absolute last resort you can clear out your current gnome settings, which will pretty much reset your desktop back to the way it was when you installed Ubuntu.  To do this first log out of gnome so you're back at the GDM prompt.  Then hit Ctrl-Alt-F1 to get to a text console and log in with your regular username/password.

Now run:

rm -Rf .gnome* .gconf* 

You can then hit Ctrl-D to log off the text console and Ctrl-Alt-F7 to get back to GDM.  Log in and the system should set you back up with the default desktop.

---

### Post by sdim on 2007-08-23
Now I indeed have the default desktop,but APPLICATIONS _still don't show anything_!
Now I'm starting to panic...I can't find any of my applications...It seems that this was the end of my experience of Ubuntu...
Thanks for the tip,though.

---

### Post by gashcrumb on 2007-08-23
Strange...  Can you hit Alt-F2 again, type gnome-terminal and then cd to /etc/xdg and see if there's anything under that directory?  I thought thow that customizations to the main menu wound up under ~/.gconf or ~/.gconfd.

As yet another last resort you can always create a new user account and then log in with that user account.  Just go to System/Administration and select "Users and Groups", then click "Add User", give it a different username, fill in the password etc., then go into the "User Privileges" tab and make sure "Administer the system" is checked so this user can use "sudo".  Then log off and log on as that new user.

---

### Post by sdim on 2007-08-23
This is what I found out...
I think it's time to re-install Ubuntu...
Thanks for all the help,man.I really appreciate your wiilingness.

---


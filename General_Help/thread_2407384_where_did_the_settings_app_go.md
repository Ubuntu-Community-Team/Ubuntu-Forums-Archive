---
title: "where did the settings app go?"
date: 2018-12-03
forum: General Help
---

### Post by hmiersch on 2018-12-03
when i tried to upgrade from 18.04 to 18.10, something went wrong and i ended up having to reinstall ubuntu. after that i used the settings app to set up the system, create my user account, configure the network, the whole nine yards. so far so good. 
yesterday i wanted to use that same settings app for something, and i realized that it has disappeared. i can't find it in my user account, i can't find it in my admin account, and i can't find it in ubuntu software either. in other words, i used it not so long ago and now it's gone. what's going on? where did it go?

---

### Post by Dennis N on 2018-12-03
Did you use the Search box to find what you want?

Super Key > enter "settings" in search box.

Should find the dialog for you.

---

### Post by hmiersch on 2018-12-04
i tried searching but it gave me all kinds of files and folders whose names contain "settings". but there are so many of them. c++ files, header files, other files... a needle in a haystack comes to mind.

BTW, did i mention that when i go to the menu in the top right of the screen and select the network settings, nothing happens? that means that something has gone haywire...

---

### Post by dragonfly41 on 2018-12-04
I have looked in my Ubuntu 16.04 and I can launch Settings panel
by clicking on
/usr/bin/unity-control-center

It seems that "unity-control-center" is what you should search for

sudo locate unity-control-center

---

### Post by maglin2 on 2018-12-04
Are you perhaps thinking of the Initial Setup app?
I suspect it is configured to only run once per account, but I guess you could run it again? Not really sure what it does that you can't also do under the other standard System Settings sections though.
I use 18.04 Gnome Flashback. It doesn't show up for me unless I go to Main Menu and select it under System Tools.

---

### Post by deadflowr on 2018-12-04
> **dragonfly41 said:**
> I have looked in my Ubuntu 16.04 and I can launch Settings panel
by clicking on
/usr/bin/unity-control-center

It seems that "unity-control-center" is what you should search for

sudo locate unity-control-center

On 18.04 just switch out unity for gnome, like gnome-control-center.

A thought is to check if it's user related.

One thing you can do is create a simple user; just use adduser.
Then logout and at the login screen choose the new user.
Then see if that new user has the same problem or not.
If not then your main user has something amiss.

If it still has issues then try reinstalling the package (name same as above)

But it's best to check if it's a user problem first or else reinstalling won't do anything helpful.
(Not helpful because users have their own independent configuration settings which aren't affected by packages being installed and removed.
Those you need to deal with yourself, manually. (But that usually means either a simple dconf reset or a file/folder removal))

---


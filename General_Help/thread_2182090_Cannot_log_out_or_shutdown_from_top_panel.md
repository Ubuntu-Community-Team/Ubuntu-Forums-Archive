---
title: "Cannot log out or shutdown from top panel"
date: 2013-10-20
forum: General Help
---

### Post by mickee384 on 2013-10-20
Hey all! Since I updated to 13.10, I have been unable to either log out or shut down from the top panel. I can lock the session though. I can still shut down or reboot thru the terminal. When I choose either of teh two options, nothing happens. Any body else have this?

---

### Post by carl4926 on 2013-10-20
No
Did you test a new user?

---

### Post by mickee384 on 2013-10-20
Good idea! Ok, so I can switch users to my son's account and the logout/shutdown works. Also he is a standard user, and I am admin

---

### Post by carl4926 on 2013-10-20
> **mickee384 said:**
> Good idea! Ok, so I can switch users to my son's account and the logout/shutdown works. Also he is a standard user, and I am admin

Sounds like something go messed up in your hidden user settings. I really can't tell you where and my solution would likely be overkill.
See if any one else has a bright idea

---

### Post by mickee384 on 2013-10-20
Thanks for the idea. Will look at permissions. I will post back what I  can, but am still looking for an answer (i'm not really strong in terminal)

---

### Post by mickee384 on 2013-10-22
so interesting... I can shutdown, log out and restart using the add on "classic menu indicator" (system settings), also if I use the same features in the dash. Just can't activate these from the panel. From the panel I can suspend or lock. I checked the logs, i'm not seeing that the clicks on shutdown for example do anything at all under my user. (works on another user, they are standard, I am admin)

---

### Post by Cavsfan on 2013-10-22
I have the same problem with Saucy 13.10. In Gnome Flashback the button in the top right panel will allow me to logout and suspend but, that is all. Sometimes there is a restart option but it won't restart.
Other times there is just a shutdown option and it doesn't work either. 

I use the logout button from Cairo Dock to logout and restart.

Pretty sure this problem is limited to Gnome Flashback. I never had any problem with Unity but, I prefer Flashback.

I thought this would be fixed before final release but, it was not.

---

### Post by mickee384 on 2013-10-22
sorry, what's gnome flashback?

---

### Post by Cavsfan on 2013-10-22
> **mickee384 said:**
> sorry, what's gnome flashback?

Gnome Classic - install via **sudo apt-get install gnome-session-flashback**. Then logout and it will be one of the available sessions. It has the top and bottom panels like the previous versions of Gnome.

It went from Gnome Classic to Gnome Fallback to Gnome Flashback.

You'll need Cairo Dock too to restart, Unless you want to open terminal and enter **sudo reboot** to restart.

---

### Post by mickee384 on 2013-10-22
I see. Yeah, prior to 12.10 I had gnome as a fallback. Think they removed it from 12.10 and I don't have it now. I have the option to shutdown, restart etc thru the dash, but may be simpler to add the functionality to the cairo-dock. What I find weird is teh panel shutdown option still doesn't work, yet I can shut down using the classic indicator applet. I really am hoping to get the shut down, restart and log off available in the top panel. The buttons are functional on my son'd account and he's a limited user, whereas I am admin.

---

### Post by mickee384 on 2013-10-23
I ran gnome flashback and same issue. My user cannot shutdown, logoff or reboot. Same as with Unity. What I don't understand is why I can do all of these from the ClassicMenu Indicator add-on. I can also use cairo-dock desklet and that works as well. Just not from the main system panel.

---

### Post by mickee384 on 2013-10-23
I am hoping to have some kind of epiphany here... (still could use some help) :p

---

### Post by Cavsfan on 2013-10-23
I thought this was only happening in flashback. I didn't know it happens in Unity too.
Someone should open a bug report. I don't think one exists.

---

### Post by Cavsfan on 2013-10-23
What is so sweet about Cairo Dock whether the top button works or not is that the logout button in Cairo Dock tells you when you need to restart after a software update. ;)

---

### Post by philinux on 2013-10-23
> **mickee384 said:**
> Good idea! Ok, so I can switch users to my son's account and the logout/shutdown works. Also he is a standard user, and I am admin

Easy solution would be to create a new admin user for yourself.  Then assuming all works then just copy any profiles you need like Firefox xchat thunderbird for example to the new user. Along with any other data from your backup.

You can then delete the original admin user.

The bad settings could be in .gnome or other config folder.

---

### Post by sdowney717 on 2013-10-23
For me I notice this also.
For me it is seemingly random, sometimes it will work.

When it does not work, if I reboot either unplug it or sudo reboot, then the menus suspend and shutdown works again.

Anyone filed a bug?

---

### Post by Cavsfan on 2013-10-23
> **Cavsfan said:**
> I thought this was only happening in flashback. I didn't know it happens in Unity too.
*Someone should open a bug report. I don't think one exists*.

> **sdowney717 said:**
> For me I notice this also.
For me it is seemingly random, sometimes it will work.

When it does not work, if I reboot either unplug it or sudo reboot, then the menus suspend and shutdown works again.

Anyone filed a bug?

No I am unaware of any bug.

---

### Post by mickee384 on 2013-10-24
> **philinux said:**
> Easy solution would be to create a new admin user for yourself.  Then assuming all works then just copy any profiles you need like Firefox xchat thunderbird for example to the new user. Along with any other data from your backup.

You can then delete the original admin user.

The bad settings could be in .gnome or other config folder.

I will try to do that. But how do i know what parts of the profiles to copy that won't include gnome setting for my current user?

---

### Post by carl4926 on 2013-10-25
> **mickee384 said:**
> I will try to do that. But how do i know what parts of the profiles to copy that won't include gnome setting for my current user?

I usually keep .mozilla .thunderbird
Then inside .config and .cache I keep folders for chrome and chromium
I have a backup of my konversation settings (I use the kde chat client)

Ideally you should do the deleting from another install (I have side by side installs) or use a utility like Parted magic, I'm not 100% sure if an ubuntu live session will let you delete some of the stuff.

---

### Post by mickee384 on 2013-10-27
I use Chromium. I have all my doc and images etc in a backup plan. Can I create another user with the same name? I would think the sid would be different, then copy over all may data to the new user? Thanks for your help btw

---

### Post by Cavsfan on 2013-10-28
> **mickee384 said:**
> I use Chromium. I have all my doc and images etc in a backup plan. Can I create another user with the same name? I would think the sid would be different, then copy over all may data to the new user? Thanks for your help btw

If you want to back up your Chromium folder it is in a hidden folder in your home directory. Mine is **/home/cavsfan/.config/chromium**. Drop that into your new userid's home directory in **.config** folder and it will retain all of your settings: bookmarks, extentions, cookies, etc.
Just FYI: the folder for Firefox in in the home directory **.mozilla** and Thunderbird is in **.thunderbird**.

---


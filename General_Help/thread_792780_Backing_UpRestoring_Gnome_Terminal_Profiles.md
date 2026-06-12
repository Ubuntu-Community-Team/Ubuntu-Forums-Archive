---
title: "Backing Up/Restoring Gnome Terminal Profiles"
date: 2008-05-13
forum: General Help
---

### Post by pewterz on 2008-05-13
Hello,
I have installed Hardy on a new PC and I am slowly migrating things off of my old PC (Gutsy). I've managed to get KDE Menus, Tomboy and other application settings migrated by copying 'dot' directories over however I cannot seem to migrate my gnome-terminal profiles.

I've copied ./gconf/apps/gnome-terminal from my Gutsy PC onto my Hardy PC however the gnome-terminal still does not recognize my profiles.

Does anyone have any ideas how to both backup and restore the gnome-terminal profiles?

---

### Post by imthemp3king on 2008-07-12
Was just curious to know if you had found a solution to this issue?  I am experiencing the same thing.  I backed up my entire home directory, upgraded, and then copied over the backup of .gconf to my new Hardy install.  I can see the profiles, but they do nothing but launch a normal terminal session.  If anyone else has any ideas on how to properly backup/restore these profiles I would love to hear them.  I don't look forward to recreating 50+ profiles

---

### Post by prshah on 2008-07-12
> **pewterz said:**
> 
I've copied ./gconf/apps/gnome-terminal from my Gutsy PC onto my Hardy PC however the gnome-terminal still does not recognize my profiles.


> **imthemp3king said:**
> 
I am experiencing the same thing.  I backed up my entire home directory, upgraded, and then copied over the backup of .gconf to my new Hardy install.  I can see the profiles, but they do nothing but launch a normal terminal session.  

Just a suggestion: Your UID and/or GID may have changed, even if your username/groupname has not. Try this command, then restart gnome and check if your terminal profiles now work;

```
cd ~/.gconf/apps/gnome-terminal/
chown -c `whoami`:`whoami` *
```

---

### Post by imthemp3king on 2008-07-15
Thx for the reply prshah!  I re-copied over the contents of the ~/.gconf/apps/gnome-terminal/ folder and ran the command you suggested, but the result is the same behavior I was seeing before.

---

### Post by ajorpheus on 2008-09-18
Hi, 

Try the following steps:

1. Fire up **gconf-editor**

2. Navigate to /apps/gnome-terminal/global/profile_list

3. Edit the value of profile_list. You shall need to click on "Add" and then enter the names of each of your profiles

Let me know if this helped.

Regards,
AJ

---

### Post by mp3foley on 2009-05-14
Thanks!

Copying my old files under .gconf/apps/gnome-terminal and then using gconf-editor to add the profile_list worked for me under Jaunty.

Note, I also had to log out and log back in to get the new profiles to show up.

---

### Post by Jonathan McDowell on 2009-07-23
Thanks a million, this worked for me too... I've been searching for it ever since gnome-terminal existed.
This is still a pretty painful way to copy profiles... I miss simple old .rc files.
Now, if you can tell me how to copy launchers on gnome-panel from one installation to another,
that would be even better...

---

### Post by rhp997 on 2009-08-26
> **mp3foley said:**
> Thanks!

Copying my old files under .gconf/apps/gnome-terminal and then using gconf-editor to add the profile_list worked for me under Jaunty.

Note, I also had to log out and log back in to get the new profiles to show up.

Under Jaunty, the profiles are enumerated under /home/<user>/.gconf/apps/gnome-terminal/profiles like "Profile0", "Profile1", etc... Each profile has it's own %gconf.xml file which contains the settings.  The /home/<user>/.gconf/apps/gnome-terminal/global/%gconf.xml file *should* contain the listing of each of the profiles under /home/<user>/.gconf/apps/gnome-terminal/profiles.  You may directly edit the xml file or use gconf-editor as described above - the results should be the same (Note that the profile name and the visible name may be different).  In order to copy the profiles, you'll need to be sure that both the .../global and .../profiles folders are copied to the .gconf/apps/gnome-terminal directory under your user. I have been rolling out desktops for multiple users and I've finally been able to push specific profiles to each user by copying the two aforementioned folders to /etc/skel.  The final trick is knowing that once the user has been created for the first time, they must logout and then login before the profiles will be usable.

---

### Post by khughitt on 2009-10-11
Inspired by this process, I wrote a suggestion on Ubuntu Brainstorm ([http://brainstorm.ubuntu.com/idea/21807](http://brainstorm.ubuntu.com/idea/21807)) to suggest a simpler way to backup and restore specific gconf settings.

Check it out, and vote it up if you think it's worth-while, and feel free to add your own suggestions :)

---

### Post by spamless on 2011-01-01
> **mp3foley said:**
> Thanks!

Copying my old files under .gconf/apps/gnome-terminal and then using gconf-editor to add the profile_list worked for me under Jaunty.

Note, I also had to log out and log back in to get the new profiles to show up.

Agreed -- much obliged to **ajorpheus**.  It worked for me just the same (logout required) on Maverick.

---


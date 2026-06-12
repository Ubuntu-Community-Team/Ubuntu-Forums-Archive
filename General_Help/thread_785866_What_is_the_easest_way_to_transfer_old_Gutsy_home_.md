---
title: "What is the easest way to transfer old Gutsy home folder for use on Hardy"
date: 2008-05-07
forum: General Help
---

### Post by tebibyte on 2008-05-07
I backed up my home folder from gutsy, which I wiped and replaced with Hardy. It didn't want to do an upgrade. How do I restore all the settings from my old home folder to my new installation? I would most importantly want to salvage my firefox bookmarks, and Thunderbird emails.

Thanks for your help

---

### Post by BennBuntu on 2008-05-07
User files are kept in the .* folders in the home directory. If you want firefox, copy the .mozilla folder across. ctrl+h will let you see hidden folders in nautilus. Just pick the ones you want, pidgin is called .purple

---

### Post by jocko on 2008-05-07
The best way (in my opinion at least) is to make a separate /home partition.
That way you get to keep all settings when you reinstall, as long as you make sure to set the mount point and not re-format the /home partition during the installation.

If you just want to transfer all your settings from a backup of the old /home folder, just copy all the files and folders, including hidden ones, from the backup to the new /home folder.

---

### Post by tebibyte on 2008-05-07
I copied over all of the hidden files from my home folder, into the new one. Not all of my settings have been restored. There are three profiles in my .mozilla folder:
the 
 /home/max/.mozilla/firefox/79qkivuy.default
/home/max/.mozilla/firefox/lanyo6dt.default
/home/max/.mozilla/firefox/prk7eo0b.default

/home/max/.mozilla/firefox/profiles.ini

is set to 

Path=79qkivuy.default

so it opens up the new folder. 

I changed it to lanyo6dt.default,
but then error messages pop up.

---

### Post by tebibyte on 2008-05-07
> **jocko said:**
> The best way (in my opinion at least) is to make a separate /home partition.
That way you get to keep all settings when you reinstall, as long as you make sure to set the mount point and not re-format the /home partition during the installation.

If you just want to transfer all your settings from a backup of the old /home folder, just copy all the files and folders, including hidden ones, from the backup to the new /home folder.
That's good advice, I created a /home partition this time, but not last.

Maybe I should delete the new files, so they don't conflict.

---

### Post by jocko on 2008-05-07
If you still have the old .mozilla folder (with the profile you want), delete the new one and replace it with the old one.
Or, if it's just the bookmarks you want, you could import the old ones into the new profile (they are stored in the file ~/.mozilla/firefox/[COLOR=Gray][xxx][/COLOR].default/bookmarks.html).

---

### Post by tebibyte on 2008-05-07
> **jocko said:**
> If you still have the old .mozilla folder (with the profile you want), delete the new one and replace it with the old one.
Or, if it's just the bookmarks you want, you could import the old ones into the new profile (they are stored in the file ~/.mozilla/firefox/[COLOR=Gray][xxx][/COLOR].default/bookmarks.html).

I tried to. I got the following message:
> Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features.

The problem is that this version of firefox is newer than the one my home folder used. They won't play nice.

---

### Post by tebibyte on 2008-05-07
> **tebibyte said:**
> I tried to. I got the following message:


The problem is that this version of firefox is newer than the one my home folder used. They won't play nice.

Scratch that. It is a permissions problem. Let me fix it and see what happens...

---


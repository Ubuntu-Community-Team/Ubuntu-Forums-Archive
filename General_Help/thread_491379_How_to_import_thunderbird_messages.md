---
title: "How to import thunderbird messages"
date: 2007-07-03
forum: General Help
---

### Post by Cool Surfer on 2007-07-03
How do I import thunderbird(installed in windows xp) messages to thunderbird installed in ubuntu?

Where are email  messages stored in thunderbird in windows?:popcorn:

---

### Post by MCSE_Crossover on 2007-07-03
Enable "view hidden files and folders" under Windows

Copy all the files within the C:\Documents and Settings\"your username"\application data\thunderbird\profiles

to  

/home/"user"/.mozilla-thunderbird/profiles

.mozilla-thunderbird is a hidden directory, so make sure you are able to view it if using Nautilus/Konq

Start Thunderbird...good to go.

if you had multiple profiles set up using "Profile Manager" you will need to reconfigure them and just point them to the appropriate user directory under /home/"user"/.mozilla-thunderbird/profiles

---

### Post by davidjmayo on 2007-07-04
> Copy all the files within the C:\Documents and Settings\"your username"\application data\thunderbird\profiles

to

/home/"user"/.mozilla-thunderbird/profiles

I can copy the files from windows but there is no /home/"user"/.mozilla-thunderbird/profiles

only /home/"user"/.mozilla-thunderbird  which is were my current profile is. I copied it here but Thunderbird does not pick it up. Do I need to edit profile.ini and create a new entry?

My profile.ini as it is:

> [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=kiqs1tv5.default


kiqs1tv5.default is my ubuntu thunderbird profile

---

### Post by Cool Surfer on 2007-07-04
> **MCSE_Crossover said:**
> Enable "view hidden files and folders" under Windows

Copy all the files within the C:\Documents and Settings\"your username"\application data\thunderbird\profiles

to  

/home/"user"/.mozilla-thunderbird/profiles

.mozilla-thunderbird is a hidden directory, so make sure you are able to view it if using Nautilus/Konq

Start Thunderbird...good to go.

if you had multiple profiles set up using "Profile Manager" you will need to reconfigure them and just point them to the appropriate user directory under /home/"user"/.mozilla-thunderbird/profiles


Great!!  Thanks, it worked cool :)
All messages and folders imported.

---

### Post by Cool Surfer on 2007-07-04
> **davidjmayo said:**
> I can copy the files from windows but there is no /home/"user"/.mozilla-thunderbird/profiles

only /home/"user"/.mozilla-thunderbird  which is were my current profile is. I copied it here but Thunderbird does not pick it up. Do I need to edit profile.ini and create a new entry?

My profile.ini as it is:



kiqs1tv5.default is my ubuntu thunderbird profile
I copied the folder in which i could see my winxp email folders, to profile (NOT PROFILES) folder
in ubuntu thunderbird. Did nothing else. Closed thunderbird and restarted. And all emails were there.

---

### Post by davidjmayo on 2007-07-04
I don't have a profile directory either (if I saw that I would have tried that)

in /home/"user"/.mozilla-thunderbird all I have is 
the ubuntu .default 
the copied .default (from MS) 
appreg (shows as unknown file type!!)
profiles.ini 

and that's all. No directory for profile or profiles

EDIT: Could it be because I use global and not local folders as I only have one email account to check?

Anyway it's not important I was just checking to see if it worked.

---

### Post by Cool Surfer on 2007-07-04
I could manage to do the above to a thunderbird directory I had installed thunderbird to.
But I wanted to use default programs of ubuntu.

Where are the files of thunderbird - the one we see when we click on applications > internet > thunderbird mail

Shall appreciate. Thanks

---

### Post by Cool Surfer on 2007-07-04
> **davidjmayo said:**
> I don't have a profile directory either (if I saw that I would have tried that)

in /home/"user"/.mozilla-thunderbird all I have is 
the ubuntu .default 
the copied .default (from MS) 
appreg (shows as unknown file type!!)
profiles.ini 

and that's all. No directory for profile or profiles

EDIT: Could it be because I use global and not local folders as I only have one email account to check?

Anyway it's not important I was just checking to see if it worked.

Inside your profile folder you will see something like this- 18rkvjsy.default
copy that and paste it in profile folder in ubuntu thunderbird.

---

### Post by skeptikone on 2007-08-07
Hi All,

I have copied all of the profile info, however my emails are stored seperately in C:\Email Storage, Have tried copying these files over also into the same directory, and also a seperate directory (whilst modifying prefs.js to point to the right dir) but to no avail...

any suggestions?

a quick search of the forums yields no results.

---

### Post by Ansible on 2007-08-10
I also saw no "profiles" folder in my ".mozila-thunderbird" folder.  There was a "91m9xn1j.default" folder, an appreg file, and a profiles.ini file.  

I copied the folders from "profiles" on windows directly into ".mozilla-thunderbird".  There were two folders, named similarly to "91m9xn1j.default".  One was only 357k, the other 2.5 gigs.  I replaced "91m9xn1j.default" in the proifles.ini file with the name of 2.5 gig folder, restarted thunderbird, and there are all my accounts and messages.  Cool!

---


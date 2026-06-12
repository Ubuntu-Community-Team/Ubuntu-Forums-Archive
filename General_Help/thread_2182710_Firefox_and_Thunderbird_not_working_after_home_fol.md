---
title: "Firefox and Thunderbird not working after home folder imported from xubuntu 13.10"
date: 2013-10-22
forum: General Help
---

### Post by gadjet77 on 2013-10-22
Hi everyone, I tried to upgrade from xubuntu 13.04 to 13.10 on my Asus eee 900 but it didn't work at all, so I decided to switch to Lubuntu 13.10. The system now is far more responsive, up and running after only 15 seconds from the power on. 
However, I exported the whole home folder from the old xubuntu installation and then I imported it in the newly installed lubuntu. When I try to open Firefox, an errore message says it is impossible to load user's profile, while thunderbird doesn't load at all. Is it just a problem with the folders' permissions?
I'm not a linux expert, so I'd appreciate an answer for dummies :)

Thanx everyone for your help!

Gadjet

---

### Post by amanchesterman on 2013-10-22
I'm no expert so I can offer only limited help. I guess it might be to do with permissions, or it might be that the folder structure is different in Lubuntu and FF and TBird are looking for files that aren't there, or it might be that 13.10 installs different versions of FF and/or TBird and their requirements are different.

Anyway, what I've done successfully in the past when upgrading from one release of Xubuntu to another -- and this might work with the upgrade from Xubuntu to Lubuntu as well -- is the following:
1. Perform the upgrade and check that it's all working OK.
2. Start FF and TBird and let them create new user profiles; in the case of TBird, **don't** create any email accounts or calendar entries.
3. Replace the new profiles that have just been created with the old profiles from your previous install. That involves:
3a. Find the new user profiles. On my Xubuntu system, the FF profile is at /home/john/.mozilla/firefox/xxxxxxxx.default and the TB profile is at /home/john/.thunderbird/xxxxxxxx.default. In both cases the 'xxxxxxxx' is a random string of eight letters and numbers.
3b. Make a careful note of those strings -- or simply rename 'xxxxxxxx.default' to 'xxxxxxxx.old' in both folders.
3c. Copy your old profiles into those folders and then change the 'xxxxxxxx' part of the filenames to those you have noted -- i.e. to those just created in the new install.

Doing it that way means that all the other files needed by FF and TBird are those from the new install: the only bit you import is the actual profile itself, which in the case of FF includes your personal settings, bookmarks etc., and in the case of TBird comprises all your email accounts, saved messages, calendar entries etc.

It seems a long way round and it needs to be done carefully, but as I say it has worked well for me in the past.
Good wishes
John

---

### Post by gadjet77 on 2013-10-22
Thanx for your prompt reply, John! Unfortunately I pasted the folders in the new home before starting firefox and thunderbird for the first time. Bad mistake. I tried to move the firefox folder in another position and then restart it. The program created a new /.mozilla folder but prompted the "unable to load user profile" again. Thunderbird doesn't start at all, so I'm currently stuck. :(

Gadjet

---

### Post by fantab on 2013-10-22
> **gadjet77 said:**
> ...I exported the whole home folder from the old xubuntu installation and then I imported it in the newly installed lubuntu. When I try to open Firefox, an errore message says it is impossible to load user's profile, while thunderbird doesn't load at all. 

You cannot 'import' whole of the /home folder, especially all the (dot).files, its a bad idea. Applications are different in Xubuntu and Lubuntu.
I suggest you re-install Lubuntu.
Then Replace the folders like, Documents, Pictures etc. When you are replacing (dot).files/folders be very selective.

I also, follow amanchesterman's method of replacing .mozilla and .thunderbird folders. Mark the word "Replace", which means run Firefox and Thunderbird and let them create the .folders, then close the applications and replace the .mozilla and .thunderbird. For me the .mozilla and .thunderbird survive across the distros.

---

### Post by gadjet77 on 2013-10-22
They should survive (I did it mant times across the years) but now they  don't seem to. If I rename the old thunderbird folder in  /.thunderbird.bak and I start the application, a new /.thunderbird  folder is created but I'm trying to figure out how to import there all  the old profile settings, mails and stuff. Simply pasting the old folder  in the new xxxxxxxx.default doesn't seem to work...

Gadjet

---

### Post by Habitual on 2013-10-22
> **gadjet77 said:**
> They should survive (I did it mant times across the years) but now they  don't seem to. If I rename the old thunderbird folder in  /.thunderbird.bak and I start the application, a new /.thunderbird  folder is created but I'm trying to figure out how to import there all  the old profile settings, mails and stuff. Simply pasting the old folder  in the new xxxxxxxx.default doesn't seem to work...

Gadjet

OK. I'll attempt this one.

[LIST]
[*]Close Thunderbird. 
[*]Open your file manager and navigate to your /home/<user> directory. 
[*]Press Ctrl+H to show hidden files. 
[*]Open .thunderbird.bak in your home/<user> in the file manager. 
[*]There should be a something.[COLOR=#ff0000]**default**[/COLOR] directory there. 
[*]open it. 
[*]Press Ctrl+A to select all. 
[*]Navigate with the same file manager window to /.thunderbird 
[*]and find the something.[COLOR=#ff0000]**default**[/COLOR] in the "new" ~/.thunderbird directory and open it 
[*]Press Ctrl+V to paste those contents into the "new" /home/<user>/.thunderbird/something.[COLOR=#ff0000]**default**[/COLOR] directory, overwrite all if|when prompted. 
[*]Open Thunderbird. 
[/LIST]

IF you have more than 1 email account, then you could or should copy all the contents of .thunderbird.bak/ into the "new" .thunderbird directory, including the profile.ini
and then open Thunderbird.

Are they the same version of Thunderbird at least?

---

### Post by SeijiSensei on 2013-10-22
I smell permissions problems.  You cannot copy an old home directory to a new installation unless the user ID's align properly.

Open /home/username and check to make sure that .mozilla and .thunderbird.bak, and all their subdirectories (very important), are owned by you.  If they are not, then a quick command-line solution is:

```

cd /home/username
sudo chown username:username .mozilla .thunderbird -R

```

---


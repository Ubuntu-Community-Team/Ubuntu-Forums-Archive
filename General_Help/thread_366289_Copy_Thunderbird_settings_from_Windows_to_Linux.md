---
title: "Copy Thunderbird settings from Windows to Linux"
date: 2007-02-20
forum: General Help
---

### Post by al_scott on 2007-02-20
Hello folks. 

I'm relatively new to Linux. I have created a dual boot setup on my PC, so I can run my existing Windows 2000 installation alongside my new Ubuntu Edgy OS.

I'd like to copy my Thunderbird profile from Windows to Ubuntu, but I can't work out an easy way to do it.

Does anyone know of a step by step guide do do this? or a utility perhaps?

I also need to do the same with Firefox. I presume the procedure is similar to Thunderbird.

Thanks!

Al

---

### Post by sarc on 2007-02-20
It's very simple, just copy your profile folder to a suitable location and tell Thunderbird to use it.  Soe versione of Thunderbird and Firefox have a menu to choose the Profile folder, others use a command from the Console.   It has been described in detail on a previous post, do a search on this forum.

---

### Post by LPomfrey on 2007-02-20
Go to C:\Documents and Settings\[User Name]\Application Data\Thunderbird\Profiles\ on your windows partition and copy the folder called ########.default (where ######## is a random string.) 
Now paste the folder into /home/[User Name]/.mozilla-thunderbird on your Ubuntu partition. (You could copy it to a CD/USB thumb drive etc. in between if necessary.)
Now open up the file called /home/[User Name]/.mozilla-thunderbird/profiles.ini  in a text editor and change the line:
```
Path=xxxxxxx.default
```
(Where xxxxxxxx is again a random string.) 
To:
```
Path=########.default
```
Where ######## is the random string in the folder you just copied across.

For Firefox you would do the same but using the directories C:\Documents and Settings\[User Name]\Application Data\Firefox\Profiles\  in Windows and /home/[User Name]/.mozilla/firefox in Ubuntu.


Alternatively, if you want to access them from Windows and Ubuntu, and keep the settings the same for both, copy the ######.default folders to a folder on a partition accessible by both Windows and Ubuntu (FAT32 etc.) and change the profile.ini files to the following:
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/where/you/copied/the/folders/to/#######.default

```
Note the IsRelative line has changed. ;)
Remembering which one was the Firefox profile folder and which was the Thunderbird one obviously.

---

### Post by DJ_Peng on 2007-02-20
Please note that if you don't move the profile folder to a location on a new drive with *exactly* the same path you will do search and replace to update thelocations. You can get more iformation in [Migrating settings to a new profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile) in the Mozilla Knowledge Base.

To access the profile manager in Thunderbird you will need to run  ```
path/to/Thunderbird]/thunderbird -p
```

---

### Post by Erlander on 2007-02-21
Its a while since I did it but I'm sure all I did was to find the folder with the random string of characters in Documents & Settings/username/Application Data/Thunderbird/Profiles ,open the folder and copy its contents to a usb stick.

Then I took the usb stick to my Ubuntu pc and copied those files into a similar folder with a random string of characters as its name.

This moved all my emails, address book etc across.

Rob

---


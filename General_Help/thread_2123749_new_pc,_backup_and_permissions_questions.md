---
title: "new pc, backup and permissions questions"
date: 2013-03-08
forum: General Help
---

### Post by railz68 on 2013-03-08
hey all,

I am getting new pc next week, and i am backing up with a tar file for all of /home/me, and a copy of select files/folders into dropbox. I am still on 10.04 LTS, everything has worked fine, so i've never updated.

So, i did this once before when i got this pc and installed fresh, but can't remember. I do remember having permission issues moving old files into the new. My new pc, i will use same username and password, but i know i must claim ownership of my old files to be able to use them. I cannot remember the command(s). Could someone tell me, and also, if i run the command before or after i put the files back in place.

I am backing up hidden files too, I don't know my password on this forum, or many others, FireFox has them saved. So i need to backup these certain hidden files.

Somehow my Thunderbird mail is 2.8 gigs, and for the life of me i don't know why. I have maybe 50 to 60 emails i have kept, but doesn't justify that. They only contain text.

what files usually have or save all your settings ?. Is there a certain file extension to look for ?. If there was just one or two files to save from ./thunderbird, so that i could put it place on new PC, and my mail settings would be saved (login, pw, address book....).

Want to backup those same files for /xchat /firefox /thunderbird and a few others.

My hope is that when i install new and fresh, I am only putting back what is needed for logins and such. Not old data that is not needed, or can cause troubles.

thx for any suggestions, this is stressful.

---

### Post by jonnyboysmithy on 2013-03-08
Use Ctrl+h to show hidden files. Copy the ones you know you need. Keep the ones you don't think you need as a backup on the old pc (they may come in handy if you missed something).
Hidden folders simply have a dot  in front of the name, so the folder Stuff would not be hidden but .Stuff would be.



To get the permissions correct use your account to copy paste them, that way they inherit your permissions.

Or you can use this command: ```
sudo chown -R yourusername /home/me/example/
```
This will make you the owner of the folder /home/me/example/. That way you have permission to access and modify everything inside.

EDIT: All your firefox settings are saved in .mozilla 
You can view saved passwords and usernames under >Edit>Preferences>Security>Saved Passwords>Show Passwords

---

### Post by railz68 on 2013-03-08
thanks for the command for ownership. But for hidden files, i know how to view them. I was more looking for which ones are the important ones to backup and restore. Like for FireFox, i have my bookmarks exported and backed up. But what file contains my logins for say here on this forum. I have passwords and logins for for here, other linux sites, tech sites, photography, home theatre,.....

I am guessing its one maybe 2 important files to backup that saves these settings.

So when i have new pc with latest ubuntu installed next week, what file or files would i put back into /home/me.moziilla/firefox  so that when i visit here, it remembers my login/pw. I don't want to restore old themes and such into a new install. I just want to restore whats needed for logins. Maybe thats my cache or cookies, i am not sure.

Am i asking correctly for what i'm after ?. Excited about new pc, stressed over what I'll forget or won't be able to restore.

Edit: yes i know how to view my passwords for each site under saved passwords. But that means write them down, or copy paste them into a text file. and then enter them as each site asks for user/pw. There is one or two files that you put back into the directory, and it's done. I did this 4-5 years ago, and cannot remember how. All this information is in a file in /home somewhere. If it restore the entire ./mozilla/firefore/ back i am positive it will work. I am also sure it will also put a load of stuff back i don't want or need from 6 years ago.

Maybe it's cookies, i dunno.

---

### Post by jonnyboysmithy on 2013-03-08
After some googling I found that: Your passwords are stored in two different files, both of which are required: 
key3.db - This file stores your key database for your passwords. To  transfer saved passwords, you must copy this file along with the  following file. 
signons.sqlite - Saved passwords.

On your new install you will need to launch firefox once so that it creates a .mozilla folder with all the stuff that goes with it.
Inside  the .mozilla/firefox/  there is a folder with some weird name like  xkquzwu5.default That is your profile, and they're named differently,  your one will have a different name from mine.
Paste key3.db and signons.sqlite in there. That should do the trick.
Don't sweat it ;).

---

### Post by railz68 on 2013-03-08
ok jonnyboyssmity, that is just what i was looking to do. Exactly what i want to do. New install, launch FireFox for the first time, it creates the directories in the ./hidden folders. I then close app. Then from my backed up files use sudo chown -R on these 2 files, and put them in place. All should be good when i launch FF the next time. Then when i visit here, it auto logs me in. Or at least, it has my user/login in memory. I hope it works out just like restoring bookmarks.

If this works out, thank you so much. If i could ask what or how you searched in google, cause there are a few apps i would like to do the same thing. I have all /home backed up, but it it seems silly and destructive to just restore all back into a fresh install. I would rather just put back in place what i need.

---

### Post by jonnyboysmithy on 2013-03-08
Yea I do the same, only bring with me to the new install what I need.
I just googled "where does firefox store its saved usernames and passwords" theres a whole bunch of people who asked that very question and the answers are out there.
Look around, google some more, if you get stuck you can always post back here. :)
Good luck!

---


---
title: "Thunderbird syncing in dual boot"
date: 2007-11-09
forum: General Help
---

### Post by jfairy on 2007-11-09
Ok bear with me, Im new to command line... (been GUI's all the way for me, yes I hear your groaning from here)...
Got the dual boot Gutsy/XP box going. I have all my email on the XP side, Thunderbird of course, so Ive set up TBird in Gutsy as a new profile, & I found this how-to [http://blog.nikolaidis.com/?p=117](http://blog.nikolaidis.com/?p=117).
Basically its like this (please excuse the cut'n'paste, hope Im not treading on toes here):

ln -s /media/sda1(or Win partition of choice)/Documents and Settings/yourname/Application \
Data/Thunderbird/Profiles/xxxxxxxx.default \
~/.mozilla-thunderbird/xxxxxxx.default

ok so to me that looks pretty simple, right? (remember my exposure to terminals have been in airports....)

except this is what I get:

venus@venus:~$ ln -s /media/hda1/Documents and Settings/myname/Application \Data/Thunderbird/Profiles/s6006der.default \~/.mozilla-thunderbird/el8fq3iv.default 
ln: target `~/.mozilla-thunderbird/el8fq3iv.default' is not a directory 

so my guess is that Im leaving a space out, or putting one in where it shouldnt be, or Ive got one letter wrong, or just generally my ignorance is getting the better of me here :)

Can someone please adjust my blindfold so I have *some* idea of where to stick the pin?

cheers

---

### Post by Wyando on 2007-11-17
try without '\' before the ' ~'. Further is a space in a command line written as '\ ' instead of ' \'. Maybe this will solve the problem...

---

### Post by jfairy on 2007-11-22
Ok, thanx for that. I managed to get it sorted to the extent that it 'seemed' to work in command line (ie, it said that symbolic links were created), but the bugger is still not working for me. I tracked down the symbolic links it had set up & they appear to be 'broken'. 
Hmmmm.
The most frustrating part is that I cant find any contact details for the bloke who wrote the code in the first place, without downloading & joining up with the blog software he is using...... which Im not prepared to do as a matter of principle. 

If anybody has got this to work I would love to hear from you!

cheers

---

### Post by tenmillionmilesaway on 2007-11-22
I use the exact same profile folder in xp and gusty, create a new profile and point the folder at the same folder as you use in windows.  This should work fine since in gusty windows drives are mounted as read/write.

This way you don't need to worry about making any symlinks.

I presume you already know this since you have made a new profile but you can start the profile manager like this:

```
thunderbird -ProfileManager
```


Thanks,

Richard

---


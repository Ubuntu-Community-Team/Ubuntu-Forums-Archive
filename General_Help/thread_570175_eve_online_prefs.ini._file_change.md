---
title: "eve online prefs.ini. file change"
date: 2007-10-07
forum: General Help
---

### Post by merc1704 on 2007-10-07
eny 1 know hot to change prefs.ini. file ? 

"voiceenabled=0" to ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini

Include all three following entries in the prefs.ini file:

audio=0
audiodriver=0
voiceenabled=0

im a noob soz so if can be changed could ya make real easy for me to do plz 

im runing 
Ubuntu 6.06 "Dapper Drake" - Release i386

thx

---

### Post by wormser on 2007-10-07
You should be able to edit the prefs.ini file with gedit.

```
gedit ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini
```

Then you can add the lines and save.  I am not sure what the ""voiceenabled=0" to ~/.wine/drive_c/windows/profiles/username/Local Settings/Application Data/CCP/EVE/settings/prefs.ini" line means.  Can you post a link to the directions?

---

### Post by merc1704 on 2007-10-08
thx for answer 
but will it wipe all other info out in the file if i just put 
audio=0
audiodriver=0
voiceenabled=0

in the new fine ?

---

### Post by merc1704 on 2007-10-08
had a go i got this back 

Unexpected error: File not found

not know what going on i know i would like to open the wile up and make changes to the file but cant cos cant log in to desktop as root
ill have to try find another way ov making the changes to the file 
if i cant make the changes ill just put windiws back on my system as i like the game im trying to sort out
       thx

---


---
title: "Importing firefox data"
date: 2006-10-02
forum: General Help
---

### Post by jman623 on 2006-10-02
I just installed dapper drake on my parent's machine with a dual boot situation going. However my mom was upset because her bookmarks, and saved passwords were missing on the ubuntu so had to boot her back into Windows. Anybody have any idea how to import the firefox data on windows onto linux? I know their's some kind of html or xml file that represents the data but I am not sure where it's at or where to put it, any help would be appreciated. Thanks in advance.

---

### Post by Mr Frosti on 2006-10-02
This "profile" folder would be located at "C:\Documents and Settings/(username)/Application Data/Mozilla/Firefox/Profiles". There will be a folder with a string of letters and numbers. 

If there is more than one folder present, check the "C:\Documents and Settings/(username)/Application Data/Mozilla/Firefox/Profiles.ini" file to see which is the default.

This can be copied and pasted into the "/home/(username)/.mozilla/firefox/" folder in Linux. Make sure that you specify this folder as the default in the Profiles.ini folder.

---


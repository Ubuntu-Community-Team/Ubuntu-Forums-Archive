---
title: "howto move windows thunderbird email info to ubuntu thunderbird"
date: 2013-08-13
forum: General Help
---

### Post by jgw on 2013-08-13
I am trying to figure out howto move thunderbird data from windows to ubuntu.  Don't know where ubuntu is storing this info.  Same for firefox.  

thank you............

---

### Post by howefield on 2013-08-13
Thunderbird is ~/.thunderbird and firefox is ~/.mozilla

---

### Post by kurt18947 on 2013-08-13
You might take a look at an extension for Thunderbird, ImportExport tools.  I used it to archive emails from a lavabit account and it seems to have worked well.  I know you're supposed to be able to copy hidden folders from one to another but I've not had much success with that.  I haven't tried moving stuff from Windows to linux but seeing as it's a Thunderbird extension, I suspect it'd work in both.

---

### Post by oldfred on 2013-08-13
Years ago I created a shared NTFS data partition and put both Firefox & Thunderbird profiles into the shared partition. Then in Ubuntu I just had to edit path in profile.ini, similarly for Windows. I also copy entire profile to laptop when traveling. Laptop was also dual booted with XP and Ubuntu and had a shared NTFS data partition. Now I do not dual boot but am still using the shared NTFS partition (need to change, but have not yet). 

Thunderbird, but Firefox is similar. Howefield posted locations of profiles above. You have to boot once in each to create a default profile and then edit profile.ini to use your profile.
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---


---
title: "Cannot install Chrome after 14.04 upgrade..."
date: 2014-05-30
forum: General Help
---

### Post by John_Evans on 2014-05-30
Hey, I have a question that I hope wasn't covered elsewhere.  I just upgraded my system from 12.04 LTS to 14.04 LTS and Google Chrome doesn't work at all.  It was previously installed on my system and after the upgrade I would click the icon, the clear square around the Chrome logo would flash yellow (or red I forget) a few times (like it normally does when the program is loading) then it would stop flashing and nothing would happen.  No error messages, no nothing.  I uninstalled the version I had, downloaded the latest and greatest version and tried to reinstall.  It took forever for the authentication password window to pop up,  I typed in my password, then a few moments later I get a message saying the package was of low quality and wasn't recommened for installation.  I hit ignore and continue, after a few more moments it just flat out said installation failed.  I did not copy the error messages and I apologize for that.  I just wanted to know if anyone else has experienced this and what I could possibly do?  I've tired Chromium and Firefox, they work fine.  I'm just perplexed as to why this would happen in the first place.  Thanks.

---

### Post by Frogs Hair on 2014-05-30
Hello and Welcome

> message saying the package was of low quality and wasn't recommended for installation. This is a standard warning for non repository .deb packages from the software center. A possibility is that the profile is corrupt and the folder can be found in home/hidden folders .config/google chrome. If you remove the folder a new profile will be created when Chrome starts , but you would want save bookmarks from the folder if the list is long.

Extensions would also need to be reinstalled as well. If you sync your Chrome data you wont lose anything. You may also want to try starting Chrome from the terminal and check for errors before creating a new profile folder.

 ```
google-chrome-stable 
```

---

### Post by q64ceo on 2014-05-31
You could always try to install Chrome via Ubuntu Tweak.

---

### Post by John_Evans on 2014-06-01
Getting rid of the Chrome folder in the .config folder solved it.  Must've been something in there it didn't like.  Thanks for the advice guys, I really appreciate it!

---


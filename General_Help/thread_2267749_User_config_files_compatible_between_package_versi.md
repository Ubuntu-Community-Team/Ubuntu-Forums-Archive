---
title: "User config files compatible between package versions? How are they handled?"
date: 2015-03-03
forum: General Help
---

### Post by garycheng12 on 2015-03-03
User configuration files or files that reside in home are not removed when the package relevant to the files is removed (and as far as I know, the only way to remove them is to read documentations of the relevant package and remove them manually, if for any reason you need to remove them). 

In this extreme example: Lets say I had Firefox version 3 installed 2008 on a computer then removed it, leaving behind config files for Firefox 3. Today, I install Firefox (in its current version, Firefox version 36). Given the two versions are so far apart, are the config files between the 2 versions different in terms of the file itself (whether by name, # of config files, etc.)? Is Firefox 36 "smart enough" to deal with possibly obsolete Firefox 3 user config files by removing/replacing them with the  user config files for Firefox 36? Is there ever a concern that current user config files conflict with very old config files of the same package? 

Now let's say I never uninstalled Firefox 3 in 2008 and I kept updating Firefox up to Firefox 36. Do I now have a ton of configuration files for each version (since the philosophy of removing/purging not deleting user config files is that users may want to use the package again in the future)? I want to assume that configuration files of older version are being written by the newer version every time the newer version is installed. But given that updates may alter the *config files itself* and the *# of config file itself, *I'm not sure how Firefox (or any application) handles all these config files. I can possibly understand Firefox 36 knows how to deal with Firefox 35, but not as much Firefox 36 dealing with Firefox 3.

I can also understand if this at completely at the discretion of the developers of the software, but I hope there's a certain convention that developers agree to when it comes to this sort of thing (ex. applications on Windows are 99% of the time installed in the folder named "Program Files." When it comes to Ubuntu (or maybe Linux in general?), there are several locations and I'm not sure if there's a good reason for there to be).

This is just out of curiosity.

---

### Post by Impavidus on 2015-03-04
Usually it isn't very hard to find the user config files of any particular application. One standard location is in ~/.appname/ (the older standard), another is in ~/.config/appname/ (the more recent standard). It's up to the developers of the application to decide whether they want to use this standard, but most do. Firefox's config files are in ~/.mozilla/firefox.

Usually the new version of an application can read a config file left by an older version, and will then overwrite it with a new version. If the file's default location (or name) has changed, you may be left with an inert old config file.

---


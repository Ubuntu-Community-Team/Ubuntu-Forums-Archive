---
title: "Defaul firefox and user problems"
date: 2005-08-19
forum: General Help
---

### Post by Omnios on 2005-08-19
Hi I have a problem with firefox. There was a power outage cuased by a lightning storm. A few hours later I rebooted the computer and whent to log into Firefox which launched a user window and a message that my default user was in use which it was not. Anyways I turned off the ask thing user prompt to try to force it to use defauld which didnt work now Im stuck in a user account without my bookmarks settings and Extentions. 

 Anyways I need to figure out how to make it so I can choose what account to log into so I can figure out why its saying its in use.

---

### Post by GrammatonCleric on 2005-08-19
Well you could try the following but you will have to reinstall your extenstions. 

I'd just backup your .mozilla directory...

Code:

tar cz .mozilla > mozilla.backup.tgz

Then rename the .mozilla directory.

Code:

mv .mozilla old_mozilla


Now launch Firefox again.  This will build a whole new Firfox profile.

Now close firefox.   

Next select PLACES -> HOME FOLDER

Browse into the old_mozilla/firefox/2eteumik.default.  The 2eeumik.default will a unquiy named directory for your profile.  Within that directory copy the bookmarks.html file.

Browse back to you home folder and press ctrl+h, this will show all hidden directories.  

Browse into the .mozilla/firefox

Now you'll see another unquily names directory  *****.default open that.

Within that directory paste your copied bookmarks.html.

Now launch FireFox you should have all your bookmarks but now you'll need to reinstall all you extensions.

GC.

---


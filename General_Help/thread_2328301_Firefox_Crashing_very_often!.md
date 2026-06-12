---
title: "Firefox Crashing very often!"
date: 2016-06-19
forum: General Help
---

### Post by tyler102 on 2016-06-19
Ive been using ubuntu and firefox exclusively for over 5 years now and ive never seen firefox crash so much.
if its a crappy weather weekend and im online most of the day it seems firefox will crash every 1-2 hrs
if it doesnt crash it definitely locks up especially when i have several windows open usually including a youtube video

this has been happening with 14.04 lts and now just as much with 16.04 lts

i haveonly  the following ad ons installed; 
 youtube hd ,
 ad block plus,
 ublock origin,
 adblocker ultimate ,
 dark background/light letters
and weather forecast

are any of these known to be buggy by themselves or together with other ad ons?

If im stuck with a slow internet connection is youtube HD going to make that worse when i watch videos?

---

### Post by &amp;KyT$0P# on 2016-06-19
Are you using the Ubuntu's distribution build of Firefox or the official Mozilla build?

Given the large number of crashes, your Firefox profile might be corrupt.  Before starting to troubleshoot, completely quit Firefox and make a backup of your entire Firefox [profile]("http://kb.mozillazine.org/Profile"), just in case...

Try creating a new Firefox profile.  Install only the following of the extensions you have:
youtube hd ,
ublock origin,
dark background/light letters
and weather forecast

Does the crashing persist?

(Multiple ad block type extensions are known to cause conflict with each other, that's why trying this first.  Use different types of blocking extensions together if you need the redundancy.  But I digress, let's not get into that until your main issue is sorted. ;) )


If it stops the crashing, completely quit Firefox then [transfer the data & settings]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox") that you would like to retain, into the new profile.  Pay attention, making sure to do this one thing at a time, in case somewhere along the process you notice the crashing starting again.

If on the other hand it's still crashing even before transferring your settings, then there is an extension conflict.  I would suggest to troubleshoot that kind of issue by [Standard_Diagnostic]("http://kb.mozillazine.org/Standard_diagnostic_-_Firefox"), but also make sure to try ABP or Adblocker Ultimate in place of uBlock Origin.


Oh, and one more thing...
> **if its a crappy _weather_ weekend** and im online most of the day it seems firefox will crash every 1-2 hrs
(emphasis mine)
You say this, and run a weather-related extension... :-k

If you think it could be related, try leaving weather forecast extension out of the clean profile test as well, and add it back only if the crashing does not occur.

---

### Post by tyler102 on 2016-06-19
i can probly live without most those adons except the adblockers. Previous to this year adblockplus was sufficient but lately 
my fav website inundates me with continuos popups and makes it completely useless until i installed ublock and ultimate block, but not sure which of those cured my problem.

but i will do like you say and just start from scratch with a new firefox profile.
i dont think i need  to save my profile as its very new with this new 16.04 install
So i just need some newbie type instructions on how to delete firefox and reinstall the profile etc?

lol, good point on weatherforecast  as ive found them to buggy in the past, maybe not causing crashes buggy, but wouldnt work with certain versions of firefox

---

### Post by &amp;KyT$0P# on 2016-06-19
As far as adblockers, of the ones you use I would recommend uBlock Origin if you can use it.  It has some filtering options not available in other adblockers, as well as its own filter subscriptions that use said options; this makes it more able to handle certain kinds of ads etc nicely.

> So i just need some newbie type instructions on how to delete firefox and reinstall the profile etc?
I can't give complete instructions without knowing which Firefox build you use - official Mozilla build or Ubuntu distribution build.  But either way, it should go something like this:
1) make sure Firefox is completely quit
2) open a Terminal, start Firefox with the profilemanager like so:
```
firefox -profilemanager
```
3) click "Create New", give it a unique name of your choice.  **It is very important for stability to leave the default folder location!**
4) Select that new profile, select the "Don't ask at startup" checkbox (this should be done by default), then click "Start Firefox".

You should now be in a clean profile, with your original profile left alone.  Once you have this stable and set up how you like, now that you know how to access the profile manager it should be self explanatory how to delete a profile from there should you wish to delete your old profile.

---

### Post by vasa1 on 2016-06-20
Just to add to halogen2's excellent advice, uninstalling/reinstalling isn't the best way to go about things. Mostly, it doesn't achieve much. As pointed out, problems with browsers are very often the result of what the user has done: corrupted profiles, too many extensions, etc.

A +1 for uBlock Origin. It's really powerful even in default mode. Getting to know it better is preferable to having additional blockers: [https://github.com/gorhill/uBlock/wiki](https://github.com/gorhill/uBlock/wiki)

---


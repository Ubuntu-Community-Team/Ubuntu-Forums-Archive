---
title: "[SOLVED] Firefox bookmarks aren't working"
date: 2008-06-04
forum: General Help
---

### Post by dellegazze on 2008-06-04
so i updgraded from FF3 beta 5 to release canidate 2 today, and my bookmarks, history, and back buttons stop working. Okay, cool, I think to myself, probably just a momentary problem with the new release, they'll have it fixed in a minute... I downgraded back to beta 5, and the problem's still there. any suggestions?

for the record, i'm running ubuntu Hardy on an intel santa rosa macbook, dual booting with OS X.

---

### Post by iaculallad on 2008-06-04
Try reading MozillaZine's Lost Bookmark page. Speaks on bookmark manual recovery and prevention.

[http://kb.mozillazine.org/Lost_bookmarks](http://kb.mozillazine.org/Lost_bookmarks)

---

### Post by dellegazze on 2008-06-05
none of those seem to be working for me... is there any way i can completely uninstall everything related to firefox and have a fresh install?

---

### Post by akai_kenshi on 2008-06-06
I'm having the exact same problem, but I hadn't upgraded to RC2. I think it's something related to the 2.6.24-18 Linux kernel update (or one of the updates that came at the same time). I tried reinstalling everything related to Firefox in Synaptic, no dice. I tried upgrading to FF RC2 to see if it would fix the problem, still no dice.

](*,)

---

### Post by iaculallad on 2008-06-06
> **dellegazze said:**
> none of those seem to be working for me... is there any way i can completely uninstall everything related to firefox and have a fresh install?

Drop to your terminal and perform the following:

```
sudo rm /usr/bin/firefox
sudo rm /opt/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo apt-get install firefox --reinstall
```

---

### Post by iaculallad on 2008-06-06
> **akai_kenshi said:**
> I'm having the exact same problem, but I hadn't upgraded to RC2. I think it's something related to the 2.6.24-18 Linux kernel update (or one of the updates that came at the same time). I tried reinstalling everything related to Firefox in Synaptic, no dice. I tried upgrading to FF RC2 to see if it would fix the problem, still no dice.

](*,)

Uninstall your current Firefox application and visit this site to get a stable version.

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

---

### Post by cariboo on 2008-06-06
Have you tried importing your bookmarks from the default folder it is located in .mozilla/firefox/random_string-default, where random-string is a random string of letters. For the terminal challenged just press Ctrl-h in Places-->Home Folder and all the hidden files and folders will be revealed.

Jim

---

### Post by akai_kenshi on 2008-06-07
Well, the problem was solved by doing a clean install of Ubuntu. A bit like tearing down the house to fix a clogged toilet, but I had been running 8.04 since it was in beta and reinstalling seemed to clear up a few other nagging issues.

---

### Post by kornelix on 2008-06-07
I had the problem that firefox would not save new bookmarks across a restart of firefox. The bookmarks would appear to be saved in the bookmarks drop down list but would disappear with the next restart of firefox. 

I deleted the file 
   ~/.mozilla/firefox/xxxxx.default/bookmarks.bak

and the folder 
   ~/.mozilla/firefox/xxxxx.default/bookmarkbackups

and now new bookmarks are saved normally.

I have no idea why this works, but it is somewhat easier than
reinstalling Ubuntu.

---

### Post by Tavathlon on 2008-06-11
Bookmarks is a hell be loose, but I would be glad if it was only that. However, I also experience the same problems as the author of the thread, but that has not been addressed here properly yet: not only bookmarks are gone, but it is also impossible to use backward, forward, stop and reload buttons. When I open firefox, I get a completely blank browser that is not possible to to any changes in, for they are not being saved. Home button is possible to use, but it takes me to the firefox search page. If I look in my preferences, my old home page is in there. Also, all my bookmarks files seems to be fine, as far as I can tell anyway.

I have tried to reinstall firefox, and I do now have the firefox 3 that is in the repositories. To be honest, I don't know which version I was using before, but I guess it was the same. There was an update recently anyway, and I didn't restart the browser for a couple of days until now.

Sure, I could try to do a complete reinstall of my system, but first of all I just don't think that should be necessary for something like this, and secondly it's not really an option - I am in the middle of thesis writing and I have a lot of funky programs installed right now and no time to reinstall them...

Does anybody know anything more about this really strange firefox update thingie?

---

### Post by rubrboots on 2008-06-11
I am having the same problem. All of my bookmarks have disappeared and I can not create new ones. Tried a firefox reinstall, and deleted the files mentioned above but no such luck. I have also noticed that the browser is not saving History or my homepage. Firefox has become almost useless to me, I would love to find a solution to this problem, or even a good alternate browser suggestion.

---

### Post by rubrboots on 2008-06-11
Solved thanks to : prince_niceguy

"rename the .mozilla directory in your home to something else and then try again. That should solve the issue."

---

### Post by Tavathlon on 2008-06-11
It did fix the problem so as to make Firefox working as it should, thank you very much!

However, all the bookmarks, add-ons etc is now of course not in there, since it's a fresh firefox instead (but the info is still existing in the renamed directory). Happen to know how I can easily import those things without needing to add everything manually one by one?

---

### Post by dellegazze on 2008-06-13
Thanks for trying, guys, but nothing has worked so far...

Sorry for the long response time.

---

### Post by Tavathlon on 2008-06-13
Not the renaming of the folder either? That worked for me. And I figured out how to get my old bookmarks back again, with the restore bookmarks from automatically generated backup files. The add-ons however, I added manually. Which wasn't so bad for me at least, since I only had one at the moment...  Can imagine that would be worse for others.

---

### Post by dellegazze on 2008-06-13
Oh wait, my bad, missed the second page. It worked! Thanks so much. Ubuntu is now preferable over OS X.

Sorry about the confusion.

---


---
title: "Clear .Cache automatically"
date: 2015-12-15
forum: General Help
---

### Post by Chelidze on 2015-12-15
This is what happened to me.

I have ubuntu 14.04 installed for some time [June 9]

I have not payed to much attention to the hdd space but I could tell that it was shrinking, naturally I blamed updates of software system etc..

Yesterday I opened .cache folder and found out it was full with videos that I watched online.

So why doesn't ubuntu auto cleans this files automatically and if it doesn't if there is a commend that I can use to clean this files?

ubuntu teaks didn't clear this files

---

### Post by speartip on 2015-12-15
I find bleachbit a useful tool for clearing unwanted files. It's in the repos.
Be careful though what you tick to be cleaned.
Personally I leave all the "Deep Scan" section unticked, also in "System" I leave, custom, memory, & free disk space unticked. You may also wish to untick all passwords as well otherwise you will have to reenter them. 
It does reclaim a lot of space though, & personally I have had no issues using it for the past 3 years.

---

### Post by vasa1 on 2015-12-15
Could you post the output of **du -h ~/.cache**?

---

### Post by ian-weisser on 2015-12-15
> **Chelidze said:**
> So why doesn't ubuntu auto cleans this files automatically[...]?

It's generally the responsiblity of the caching application, not the Operating System, to clear out it's old files.
Have you checked your application's settings?

For example, in Firefox the application cache settings are in Preferences --> Advanced --> Network tab.

---

### Post by Chelidze on 2015-12-15
**Sorry every one for late replies **

> **speartip said:**
> I find bleachbit a useful tool for clearing unwanted files. It's in the repos.
Be careful though what you tick to be cleaned.
Personally I leave all the "Deep Scan" section unticked, also in "System" I leave, custom, memory, & free disk space unticked. You may also wish to untick all passwords as well otherwise you will have to reenter them. 
It does reclaim a lot of space though, & personally I have had no issues using it for the past 3 years.

Great app cleaned everything, totally forgot about it

> **vasa1 said:**
> Could you post the output of **du -h ~/.cache**?

sadly bleachbit cleaned the whole even . cache file  

> **ian-weisser said:**
> It's generally the responsiblity of the caching application, not the Operating System, to clear out it's old files.
Have you checked your application's settings?

For example, in Firefox the application cache settings are in Preferences --> Advanced --> Network tab.

Well to be honest I don't have flash installed and firefox sometimes starts video throe totem or vlc plug in those were the files that gunked up the folder

---

### Post by vasa1 on 2015-12-15
> **ian-weisser said:**
> It's generally the responsiblity of the caching application, not the Operating System, to clear out it's old files.
Have you checked your application's settings?

For example, in Firefox the application cache settings are in Preferences --> Advanced --> Network tab.
Or you could use *Control+Shift+Delete* to bring up a screen with cache cleaning options. The key combo works for both Firefox and Google Chrome.

---

### Post by deadflowr on 2015-12-15
For what it's worth you can set both Chrome and Firefox to clear the cache on exit.
Chrome: settings >> show advanced settings >> Privacy (Content Settings) >> The top field (Under Cookies) change it to the one for Keep local data only until you close the browser.

For Firefox: Preferences >> Privacy >> In History where it says Firefox will:(the default will be remember history) toggle it to set custom settings >> Then enable the clear history when Firefox closes, and then go into the settings button in that same line, and you can pick and choose what to clear.

---

### Post by Chelidze on 2015-12-17
> **deadflowr said:**
> For what it's worth you can set both Chrome and Firefox to clear the cache on exit.
Chrome: settings >> show advanced settings >> Privacy (Content Settings) >> The top field (Under Cookies) change it to the one for Keep local data only until you close the browser.

For Firefox: Preferences >> Privacy >> In History where it says Firefox will:(the default will be remember history) toggle it to set custom settings >> Then enable the clear history when Firefox closes, and then go into the settings button in that same line, and you can pick and choose what to clear.

But are those videos files handled by firefox or plugin like totem or vlc I don't which one does it run, it says allow vlc plugin but looks like totem

---


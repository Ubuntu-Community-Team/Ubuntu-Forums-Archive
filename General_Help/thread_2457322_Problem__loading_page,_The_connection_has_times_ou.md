---
title: "Problem  loading page, The connection has times out"
date: 2021-01-30
forum: General Help
---

### Post by m3s4r00ts on 2021-01-30
Over time, i began having trouble with a 20.10 setup i've been running for a few months, and was not able to open webpages using Firefox. YouTube works, but most everything else does not. Even a simple Cat search would time out. 

I tried looking it up and found a few forums, tried some Terminal Kung Fu, with no success. I wiped the drive, and reinstalled 20.04, and searched Cats, and was glad to see it worked.

It has only been a few days, and i am now having the same problem with this pc (Thinkpad e590, yes, it's not a good pc and i will consider it as the problem). I have tried updating the pc both with Sudo apt update/ upgrade and using Ubuntu Software Updater GUI. Cant open Firefox Sync to sign in an install addons or anything. YouTube works.

---

### Post by deadflowr on 2021-01-30
Firefox defaults to using DOS (DNS over HTTPS) this uses a provider such as Cloudflare.
So that might be something to look into.
The setting can be changed in Preferences >> General >> Scroll down to Network Settings and click on Settings
Then scroll down to the bottom of the new Settings window.
You can either try disabling it or try switching Providers.

See if that helps or changes things up.
If not you can just reset things back to as they were.

---

### Post by m3s4r00ts on 2021-01-31
I tried that and the setting you referred to was already disabed by default. I forgot to mention but before coming to the forum, i tried to change the search provider from Startpage, which is my default go to, to DuckDuckGo, and after your comment i tried Bing. After loading bing, cats worked but only after a few hours, it is now completely useless, and would not load the Firefox Sync. BTW im using Arch linux for the laptop which is my daily driver and am not having this issue at all. 
Something really odd about this in my opinion.

---


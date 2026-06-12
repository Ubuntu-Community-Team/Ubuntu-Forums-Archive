---
title: "firefox web broswer is too slow"
date: 2016-01-19
forum: General Help
---

### Post by alo12 on 2016-01-19
Hi,

Since i have installed the xubuntu 14.04 lts(i have all the updates installed) firefox is very slow and sometimes the screen freezes.What coould be wrong. 

Thank you in advance

---

### Post by yoshii on 2016-01-19
That seems like it might be a RAM issue.  How much RAM does your hardare have?  
Also, in Firefox preferences you could increase the amount of disk caching it does.  I have mine set to 1024 MB instead of the default.  This will cause it to read old files off the harddrive instead of always trying to get them from the internet.  New files will still be downloaded though.  Also, be sure to set the privacy settings to NOT delete the cache on shutdown.  You can still manually delete the cache from the normal dropdown menu if you need to for privacy reasons.  But preventing it from deleting the cache on shutdown means that the cache will grow as time goes on, and you might experience a slight speed increase.  

Also, you may want to start implementing some privacy and adblocking addons so that there's less interaction with advertising websites.  This can also increase your browsing speed.  

And in the Extensions preferences, you may want to set the video plugins to Ask before activating instead of automatically running.  This might help save some RAM also.

---

### Post by SeijiSensei on 2016-01-19
Do you see a relationship between the number of tabs you have open and the performance of Firefox?  If you close a bunch of unused tabs, especially ones with dormant Flash or other video sessions, does that help?

---

### Post by Sweet_Baby_Jamie on 2016-01-20
I'm getting to know the **Midori** browser a little bit.  It's the Xfce project's very own browser and it's screaming fast, has lots of options.  I'm also a big fan of **Seamonkey** - a lesser-known Mozilla product built from the ashes of the old Netscape Suite.  Kinda like Firefox and Thunderbird all-in-one but better and faster than Opera.  It's the choice of many "light weight" distros, including Puppy and LXLE.

---

### Post by alo12 on 2016-01-20
thank you all for your answers. My system runs with a 4 gb ram. I do not believe that the problem has to do with the number of tabs as even with one tab i have problems. i have also set the broswer to delete history after the shut down now i have switch this utility off

---

### Post by yoshii on 2016-01-20
you can still delete the history and forms history without deleting the cache in firefox.  check the preferences.

---


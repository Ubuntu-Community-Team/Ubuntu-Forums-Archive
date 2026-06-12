---
title: "Exporting Firefox bookmarks from Windows XP to Linux"
date: 2008-05-06
forum: General Help
---

### Post by wyzwyk on 2008-05-06
At the present time I am solely a Windows XP user, however an ever increasing dissatisfaction with M$ products has me looking for an alternative.  Some of my more computer knowledgable friends told me about Linux and some of the more user friendly distos for newbies. After doing some homework I decided that I would like to install the Ubuntu spin-off Linux Mint in a dual boot configuration with Windows XP.  Here is my problem.  I am using Firefox 2 and have 26,000 bookmarks I want to export to the Firefox browser in Linux Mint.  How is this done?  The dual boot configuration will be on one large hard drive.

---

### Post by ryanhaigh on 2008-05-06
You can actually import all your firefox data, not just bookmarks but also passwords and other things by copying over your entire profile.

[This page]("http://support.mozilla.com/en-US/kb/Profiles") has info on where your profile information is stored for windows, linux and even mac. Basically if you copy the xxxxxxx.default directory which contains your bookmarks etc as well as profiles.ini which tells firefox which profile to use into the corresponding location on your linux system (discussed in the above link) you will have all your bookmarks and other information. If however you ONLY want the bookmarks you should just copy the bookmarks.html file from your xxxxxx.default directory to the corresponding directory on your linux install. If you are going to be switching between oses on a regular basis you may want to consider using a bookmark syncing extension there are plenty to choose from.

EDIT: if you are using hardy which comes with firefox 3 the bookmarks may be stored in an alternate location, from what i have read they are now in a database. If you copy your entire profile over firefox 3 will probably convert your existing bookmarks and other profile data but I don't think copying bookmarks.html would work in this situation.

---

### Post by IanW on 2008-05-06
Or you could use a Firefox extension called (unsurprisingly) "Password Exporter".

---

### Post by ejay563 on 2008-05-06
Yet another option is to have a small fat32 partition, and put your firefox profile on it, and point firefox to read from that profile in both windows and linux. I do this with my e-mail, but prefer to keep my firefox profiles separate because of some issues with extensions (like mediaconnectivity using different players in each os, and minimize to tray not working in linux), but if that's not an issue, I'd reccommend this way. One caution is that you should be sure to shut down the os all they way when switching between windows and linux to avoid corruption of data. 

a guide of how to do this can be found here:
[http://ubuntuforums.org/showthread.php?t=203524](http://ubuntuforums.org/showthread.php?t=203524)

---

### Post by ryanhaigh on 2008-05-06
ejay563 I just wanted to point out that there is a replacement for minimize to tray for the Linux platform called firetray [https://addons.mozilla.org/en-US/firefox/addon/4868](https://addons.mozilla.org/en-US/firefox/addon/4868), just incase you didn't know. Closing and reopenning the browser was always pointless to me so I was very happy to see this released.

---


---
title: "Moving Bookmarks from XP to Dapper?"
date: 2007-05-01
forum: General Help
---

### Post by Chappy7777 on 2007-05-01
Being a nearly noob to Linux, I have figured out a work around so that I can see my W-XP Firefox Bookmarks in Ubuntu 6.06

How do I get the Bookmarks.html file from Windows XP to Ubuntu's Firefox? I know how to find the bookmarks in XP. I back them up on a Floppy every month or so. But I have not yet figured out how to move the file from my Home/ss55 Folder in 6.06 to Firefox. 

So, can someone give me simple to understand instructions on how to do this manouver? please.

Thnx, Chappy

---

### Post by tgm4883 on 2007-05-01
the bookmarks are in a subfolder of your .mozilla folder

Or an easier way I think would be to use foxmarks

---

### Post by Chappy7777 on 2007-05-01
tgm, are you saying that I should move my XP/FFox Bookmarks.html file to a similar file in Ubuntu's FFox/Mozillafolder?  

I am not sure which version (XP or Ubuntu) of bookmarks you are saying to move. I never heard of foxmarks.

Thnx for replying,
Chap

---

### Post by tgm4883 on 2007-05-01
The bookmarks file for firefox is kept in the folder i mentioned.  You can also change the location of it is about:config.

Foxmarks is a plugin for firefox that syncs your bookmarks to their server.  I use to use it when I dualbooted to keep both my windows and ubuntu bookmarks synchronized, but now i use it to keep my desktop and laptop synchronized.

Heres a link
[https://addons.mozilla.org/en-US/firefox/addon/2410](https://addons.mozilla.org/en-US/firefox/addon/2410)

---

### Post by Chappy7777 on 2007-05-02
thnx tgm,

I think foxmarks looks like the answer and have installed it on my XP PC, and have set up the account on their website. Again, thnx for the tip.

Chappy

---

### Post by Efwis on 2007-05-02
an easy way to put your XP firefox bookmarks on your Ubuntu FF is by doing the following

if you have ubuntu set up to read from Windows XP, open the drive, navigate to documents and settings->your user name->application data->Mozilla->Firefox->Profiles->*.default and copy your bookmarks.html

next in Nuatilus hit ctrl-h to show hidden files and navigate to .mozilla->profile->*.default then you can paste your bookmarks.html file in it. restart FF and your bookmarks will be in place.

If you prefer to use Terminal to do it then copy the bookmarks.html file to a location like your desktop and enter the following commands, replace Desktop with your location to chose to copy it to.
```

cd ~/Desktop
sudo cp /home/username/Desktop/bookmarks.html /home/username/.mozilla/profile/*.default/bookmarks.html
```
I use the "*" to denote the string of letters and numbers that FF has. For example my default listing is 7tro5m0v.default

also change username to your login name.

---


---
title: "Lost all my firefox bookmarks :("
date: 2006-11-02
forum: General Help
---

### Post by p.i.m.p on 2006-11-02
im using firefox 2 on edgy.. i had my bookmarks full of useful links that i collected over a long period of time.. then today i reboot without touching any of firefox's settings and when i start firefox all the bookmarks are gone ](*,) absolutely empty :(

---

### Post by Rashid584 on 2006-11-02
try looking in ~/.mozilla/firefox/*.default for a bookmarks.html file. If you have more than one *.default folder in ~/.mozilla/firefox it means you have multiple profiles. Your old one should have your old bookmarks

*.default will be loads of random characters.default e.g. mine is called gnlx5j3e.default

-Rashid

---

### Post by p.i.m.p on 2006-11-02
thanks a lot... the bookmarks.html file didn't work.. neither did the backup one in the same folder.. however i noticed a folder called bookmark backups or something like that in the same folder and i was able to restore all my bookmarks using the file in that folder :D

---

### Post by Rashid584 on 2006-11-02
Excellent :D Shoulda mentioned that too, but i thought the normal bookmarks.html one would work :)

Your welcome :) Happy to help.

-Rashid

---

### Post by rockoff on 2008-04-15
Thank you very much for these clues, you saved my bacon!
My laptop blue screened yesterday and Firefox came up afterward as if it had never met me before.

On my XP system the bookmarks file is in 
C:\DocumentsandSettings\<me>\ApplicationData\Mozilla\Firefox\Profiles\xxx.default\bookmarkbackups
I reinstalled the latest valid one of these backups into Firefox by Bookmarks->Organize Bookmarks then File->Import...

Cheers ....

---

### Post by elmer_42 on 2008-04-15
If you want to use a completely automated and web-based way, try [Foxmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410"). Not only will it save your bookmarks to the web, but it will allow you to synchronize all of your bookmarks on your different computers so you can have your useful links on all of your computers.

---

### Post by geoff511 on 2008-04-24
Just installed 8.04 and frankly don't overly like it, prefer vers. 7.10
But that aside, I use foxmarks on several computers, but it won't let me install it on this new vers. Ubuntu running Firefox 3 beta 5.
Anyone got any ideas why, and how to install it, as I need my Bookmarks !!

---

### Post by p.i.m.p on 2008-04-24
Try: 
[http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta](http://lifehacker.com/355973/make-your-extensions-work-with-the-firefox-3-beta)

---

### Post by geoff511 on 2008-04-25
That was fantastic - it enabled to me add the other add-ons i required. - Thankyou.

But now i've looked closer at the Foxmarks button - it says it is for an older version of firefox ... DOH!!

Where are the bookmarks stored in Ubuntu so I can copy them off my Vista machine and onto this on ??

---

### Post by p.i.m.p on 2008-04-25
They're usually stored in 

/home/[your username]/.mozilla/firefox/[some random directory name like 9fx26myh.default]

Please note the "." before mozilla :)

---

### Post by geoff511 on 2008-04-25
Spot on ... thanks ...

---

### Post by amirman on 2008-04-26
I had the same problem. I was trying to import my bookmarks from firefox 2 in XP into firefox 3 beta in ubuntu 8.04.  The only method i tried was by importing the bookmarks.html file.  It seemed to not work no matter what i did.  I even closed firefox and reopened it but it seems that all i had to do the whole time was just reboot the computer because they're all here now.  Of course the bookmarks toolbar is a little different on firefox 3 but all i had to do was go into 'organize bookmarks' and move them to the different folder. all is well

** umm, correction. all is not well, i seemed to have lost all the bookmarks that were within folders i had created on my bookmarks toolbar while retaining the folders somehow. I'm going to try to use the method above and see where that gets me.

*** update: i updated my bookmarks by using the backup file in my xp application data folder, this seemed to work the same exact way as importing through an html file created by the 'export' feature.  It still required a reboot.  I'm going to try using the lifehacker tweak to get firefox 3 to use foxmarks and see if that works. so far it seems that importing the html file will only go 2 folders deep on the bookmarks toolbar.

**** update: the only solution that worked for me was to log into my foxmarks space on their page and import them all manually. it appears that importing bookmarks via HTML file on FF3 will only go 2 folders deep.  by the way foxmarks has a beta version of foxmarks for FF3, i signed up for it and got it but it still didn't work for those files more than 2 folders deep.

**** update: i did the lifehacker tweaks, i didn't like the fact that it compromises security features and stuff but i tried it anyway and it didn't make it any easier installing it, i'm sure i could have just downloaded the xpi file and installed it anyway but i think i'd rather just go through the pain of logging into windows, pulling my bookmarks in my bookmarks toolbar one folder outward and trying to import them again. i hope they update foxmarks soon, i have a feeling the incompatibility has to do with problems with the way firefox handles bookmarks in the beta. oh well.

**** update: i just used the new foxmarks beta and imported the all manually 1 by 1. [COLOR="DarkRed"]firefox 3 can not import bookmarks more than 3 folders deep on the bookmarks toolbar.[/COLOR]

---


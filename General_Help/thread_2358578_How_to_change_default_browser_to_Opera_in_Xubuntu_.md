---
title: "How to change default browser to Opera in Xubuntu 16.04"
date: 2017-04-14
forum: General Help
---

### Post by Ralph L on 2017-04-14
I am running Xubuntu 16.04 and have installed Opera and want to try it for a while, comparing it to Firefox.  I would like to make it the default browser during this comparison.  If I go to Main menu>Settings>Preferred Applications>Internet>Web Browser and select Opera Browser, I still get Firefox, when I click on a website in a Thunderbird email. So that obviously doesn't work; bug I guess.  If I google for an answer, I get lots of different ones.  The most elaborate one [https://askubuntu.com/questions/79305/how-do-i-change-my-default-browser/367820#367820](https://askubuntu.com/questions/79305/how-do-i-change-my-default-browser/367820#367820) says to edit ~.config/mimeapps.list as follows:```
[Default Applications]
x-scheme-handler/http=opera-browser.desktop
text/html=opera-browser.desktop
text/xml=opera-browser.desktop
application/xhtml_xml=opera-browser.desktop
image/webp=opera-browser.desktop
x-scheme-handler/https=opera-browser.desktop
x-scheme-handler/ftp=opera-browser.desktop

[Added Associations]
text/html=opera-browser.desktop;
text/xml=opera-browser.desktop;
application/xhtml_xml=opera-browser.desktop;
image/webp=opera-browser.desktop;
x-scheme-handler/https=opera-browser.desktop;
x-scheme-handler/ftp=opera-browser.desktop;

```This makes detailed changes to the mimeapps.list file, but I don't really understand it, and there should be an easier way. Anyway my questions are:
1. Are all these changes necessary?  I guess the ones to "Default Applications" makes sense, but do I have to change "Added Association" also; if so why?  Also, what are "Added Associations"????
2. I suppose in "Default Applications" I would simply change everything that says "firefox" to "opera-browser", but if I have to make changes to "Added Associations" do I leave the Firefox entries as they are and add the Opera associations. Or do I change the current Firefox "Added Associations" by substituting "opera-browser" every place I see "firefox".

Thanks to anybody that can help me.......

---

### Post by &amp;KyT$0P# on 2017-04-14
> **Ralph L said:**
> If I go to Main menu>Settings>Preferred Applications>Internet>Web Browser and select Opera Browser, I still get Firefox, when I click on a website in a Thunderbird email. 
Is Thunderbird's handler settings configured to use Opera as the browser?

---

### Post by KenUBF on 2017-04-15
Hi Ralph,

I've never used Xubuntu, but I imagine it would have the same or similar settings. There should be a Preferred Applications option where you can choose which programs you'd like to use by default. For example, to find it on my system (Ubuntu MATE) I go to System --> Preferences --> Personal --> Preferred Applications. Hopefully there is a similar menu set up on your system.

---

### Post by Ralph L on 2017-04-16
Thank you very much Halogen2.  That seemed to do the trick.  I followed the instructions in [https://community.linuxmint.com/tutorial/view/1391](https://community.linuxmint.com/tutorial/view/1391) and did the following:
1. In TB went to Edit>Preference>Advanced>General>Config Editor, and searched for: "network.protocol-handler.warn-external.".
2.  Changed the following 3 entries from false to true:
```
network.protocol-handler.warn-external.http
network.protocol-handler.warn-external.https
network.protocol-handler.warn-external.ftp
```

And also thank you KenUBF.  Yes, I did make the changes you suggested (see my original post).  It was required, but not enough.  TB also had to be changed.

---


---
title: "No You Tube Video in Gutsy"
date: 2007-12-31
forum: General Help
---

### Post by shawnchristopherconley on 2007-12-31
Hi I cant get you tube videos to play
in firefox or epiphany browsers
please advise

---

### Post by Irony on 2007-12-31
Go here;

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download option 1 and follow the instructions for option 1.

i.e. right click on the downloaded file and click extract here.

Then open up the resulting folder and find the installer file and drag it into a terminal and hit enter.

And thats it.
__________

Note video files won't play on Youtube unless you enable javascript in Firefox so check it is enabled - Edit > Preferences > Content > tick Enable Javascript

---

### Post by bapoumba on 2007-12-31
Please post the output to :
```
aptitude show flashplugin-nonfree
```

---

### Post by 7llusion on 2007-12-31
flashplugin-nonfree doesnt work in Gutsy curently because of the update Adobe made, the md5 sum is changed.
What you should do is o use Irony's method and tell that script to install flash in 
/usr/lib/firefox
Illusion

---

### Post by aimran on 2007-12-31
He might have meant that video doesn't show up but sound does for youtube.

---


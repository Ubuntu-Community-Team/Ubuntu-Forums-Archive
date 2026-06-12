---
title: "Installing HP Printer - I'm stuck at this step in the instructions"
date: 2014-12-01
forum: General Help
---

### Post by michael-piziak on 2014-12-01
I downloaded [COLOR=#000000][FONT=Arial]HPLIP 3.14.10

I then moved it from the download folder to the desktop

I then typed in:  cd Desktop

My terminal didn't respond the way the onscreen tutorial web page showed it should have.   Please see the attached screen shot of the webpages instructions and my terminal open in the top right hand with how it responded.

Please help.  I'm leaving for home tomorrow, and I would like to get this printer running on my sisters computer tonight.


[/FONT][/COLOR]

---

### Post by pqwoerituytrueiwoq on 2014-12-01
the default download location is ~/Downloads
these commands should get it going
```
cd ~/Downloads
chmod +x hplip-3.14.10.run
hplip-3.14.10.run
```

BTW that command did work exaclty as it was shown in that screenshot
your user name is 'house' in that screenshot the user name is 'user'
your system name is 'house-KJ294AA-ABA-m9252p' and in the screenshot the system name is 'host'

---

### Post by michael-piziak on 2014-12-01
Thank you
Marking this thead as solved.  Printer works and even the scanner on it works !

---


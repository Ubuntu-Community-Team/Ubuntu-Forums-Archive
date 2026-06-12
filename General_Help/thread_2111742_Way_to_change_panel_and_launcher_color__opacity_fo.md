---
title: "Way to change panel and launcher color / opacity for ubuntu 12.10?"
date: 2013-02-02
forum: General Help
---

### Post by symaticc on 2013-02-02
I've tried ccsm and ubuntu tweak and there is an option to change the opacity but even when I set the opacity to 0 on both, the launcher is still not fully transperant. The panel however, becomes fully transparent, which is good, but the launcher still doesn't get fully transperant. Is there any way to change the color / transparency of the launcher or panel?

Thanks in advance!

---

### Post by raja.genupula on 2013-02-02
Use MyUnity application. Its the best one I ever found. I am sure thats going to help you.

---

### Post by arpanaut on 2013-02-02
From what I understand, My Unity has not been revised to work with 12.10.
Something to do with the move from gconf to dconf.

This may have changed since I last ran 12.10 some months ago.

---

### Post by mc4man on 2013-02-02
If you want a fully transparent launcher in 12.10 - 
Open ccsm (compizconfig-settings-manager
Unity plugin > Experimental >  Background color - leave or set to 
color name - #000000
Set the opacity to **any value above 0**
(this opacity setting of greater than 0 for the custom color will not affect the launcher in terms of opacity. It will affect the Dash if using the 'no blur' option, the higher the number the darker the Dash

Edit: obviously after the above you need to lower the 'launcher opacity' to 0.0000

---

### Post by symaticc on 2013-02-03
Yes, myUnity has not been revised tro work for 12.10. 
MC4MAN's reply worked perfectly! Thanks for that!

---

### Post by Frogs Hair on 2013-02-03
UnSettings is a replacement for MyUnity on 12.10. 
 [http://www.omgubuntu.co.uk/2012/11/unsettings-a-comprehensive-tweaking-tool-for-unity](http://www.omgubuntu.co.uk/2012/11/unsettings-a-comprehensive-tweaking-tool-for-unity)

---


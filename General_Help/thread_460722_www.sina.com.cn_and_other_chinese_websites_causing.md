---
title: "www.sina.com.cn and other chinese websites causing problems"
date: 2007-05-31
forum: General Help
---

### Post by Echow on 2007-05-31
Hi all when I visit [www.sina.com.cn](www.sina.com.cn) (doesnt matter whether in opera or firefox) the desktop flickers multiple times and then the titlebar disappears on all my apps, and I cannot move or quit apps from the bottom bar (using gnome). I would give a screen shot but I can't do that either after I visit the site. Also I cannot use the System>Preferences>Windows program (probably related somehow):

Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool

The only way I can get the titlebar back is to enable and disable desktop effects (I normally have then disabled). Then everything is back to normal again (provided I keep the chinese website closed).
Anyone able to help me out?
Thanks,
Ed
Edit: Ok this site also gives me trouble:
[http://homepage3.nifty.com/blacksword/](http://homepage3.nifty.com/blacksword/)
But strangely enough this site is ok:
[http://www.geocities.jp/aoyoume/aotuv/](http://www.geocities.jp/aoyoume/aotuv/)
They are both japanese. Hrmmmm.

---

### Post by Echow on 2007-06-01
I think I have discovered the problem!
The title bar (regardless of application) is unable to display Chinese characters (or Japanese for that matter). I tested using the scmi and if I try to change hotkeys for Chinese pinyin it would screw up. I would assume that the first 2 websites have Chinese titles as well. Now anyone know how I might be able to fix this??
Ed

---

### Post by Echow on 2007-06-02
Well I just discovered it was directly related to my installation of newer libcairos etc for smoother fonts:
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)
I guess you just can't have both....:(
Ed

---


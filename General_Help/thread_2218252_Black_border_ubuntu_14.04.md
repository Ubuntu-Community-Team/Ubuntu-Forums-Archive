---
title: "Black border ubuntu 14.04"
date: 2014-04-20
forum: General Help
---

### Post by andres9854 on 2014-04-20
Hello sorry for my bad english 
Install ubuntu 14.04 in my laptop y after turn on mi pc appear 
[http://sia1.subirimagenes.net/img/2014/04/18/140418102106947149.png](http://sia1.subirimagenes.net/img/2014/04/18/140418102106947149.png)[COLOR=#222222][FONT=Verdana] [/FONT][/COLOR]
Please help me i'm newbie in ubuntu thanks

---

### Post by shadytv on 2014-04-20
This looks like an issue with Xorg so have you tried logging out then back in to see if that will resolve the issue?

if that doesn't work you can always try reinstalling "ubuntu-desktop"

simply press ctrl-alt-f2 (you'll be brought to a command line)
type in your username and press enter
then type in your password (won't display while typing) and press enter

Then you should be brought to a command line that will look like:

```
yourname@yourmachine:~$
```

from here you can type:
```

sudo apt-get purge ubuntu-desktop -y
sudo apt-get clean
sudo apt-get install ubuntu-desktop -y

```

Hopefully this will help.

---

### Post by andres9854 on 2014-04-20
Thanks for answer but follow this comands and not working

Install again ubuntu and now works fine

---

### Post by silverslimer on 2014-05-17
I get the exact same thing and it's fixed when I log out and back on but I'd like to avoid having to do that. Is there a permanent solution? I assume it has to do with Compiz.

---

### Post by paullangdon678-1 on 2014-05-28
I have the same issue. Similar  to silverslimer I can get it to go away but it keeps coming back........

---

### Post by silverslimer on 2014-06-20
The best solution, for me anyway, is to CTRL-ALT-F1 a session where the borders are black and then CTRL-ALT-F7 to return. It takes about 3 seconds and allows for Compiz (I assume that's what's used) to refresh and bring the desktop back to its normal state.

---

### Post by cigtoxdoc on 2014-10-15
I just posted same problem.  I tried youir solution.  It worked.

John

---


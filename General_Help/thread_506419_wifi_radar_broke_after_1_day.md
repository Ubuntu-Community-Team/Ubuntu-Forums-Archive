---
title: "wifi radar broke after 1 day"
date: 2007-07-21
forum: General Help
---

### Post by bishop9226 on 2007-07-21
i installed wifi radar because the stupid wireless that ubuntu comes with doesnt connect.  anyway i was happy with wifi radar and it was working last night.  then i turn on my laptop today and when i click on the icon it makes me enter my password as usual, then on the taskbar you see the "starting wifi radar" pop up for about .5 seconds and then it just goes away and nothing happens.  now im stuck using xp just so i can get on wifi.  aspdokaspokdsad

how do i remove it so i can install it again?  any other ideas besides that?  

i tried doing 

sudo wifi-radar 

in terminal and it gave me an error but i dont even know if you can open it that way.  ill paste it here in a few.

---

### Post by jimbob on 2007-07-21
I tried wifi-radar and wasn't happy with it either.  I would suggest removing it ( apt-get remove --purge wifi-radar ) and installing Wicd instead.  Works much better for me.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by bishop9226 on 2007-07-21
thanks ill give that a try!

---

### Post by feelie88 on 2007-07-23
how is it compared to wifiradar?

also, is it compatible with the rt61 driver?

---

### Post by imdano on 2007-07-23
The current stable release won't work with the rt61 (unless you're using the serialmonkey rt2x00 driver), but we're testing a new version with support for rt* cards added that people  have had success with.  You can wait for the next experimental release to try it yourself or grab it off our svn.

---


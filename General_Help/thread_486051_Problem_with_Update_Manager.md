---
title: "Problem with Update Manager"
date: 2007-06-27
forum: General Help
---

### Post by helliewm on 2007-06-27
I have lost the notification manager to tell me when I have new Updates. Additionally when I go into Update Manager to update it will not update. dpkg  --configure -a shows nothing.

The only way I can install the updates is by CLI sudo apt-get upgrade then sudo apt-get  upgrade.

This is really annoying. Anyone any ideas?   

Helen

---

### Post by jimbob on 2007-06-27
You may have just lost the notification area - happened to me once.

First see if it is installed :  *[COLOR="Blue"]apt-cache policy update-manage[/COLOR]*r

If it is, right click on your top panel and select 'add to panel' then at the bottom select notification area and OK.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by bigken on 2007-06-28
> **helliewm said:**
> I have lost the notification manager to tell me when I have new Updates. Additionally when I go into Update Manager to update it will not update. dpkg  --configure -a shows nothing.

The only way I can install the updates is by CLI sudo apt-get upgrade then sudo apt-get  upgrade.

This is really annoying. Anyone any ideas?   

Helen

have you run sudo dpkg  --configure -a

---


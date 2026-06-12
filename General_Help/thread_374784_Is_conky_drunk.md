---
title: "Is conky drunk?"
date: 2007-03-02
forum: General Help
---

### Post by raffytaffy on 2007-03-02
I rescently added another external HD to my collection...so i add the HD values to the conky script like this :

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
sda1:  ${fs_free_perc /media/My Book}%   ${fs_bar 6 /media/My Book}$color
sdb1:  ${fs_free_perc /media/WD Combo}%   ${fs_bar 6 /media/WD Combo}
sdc1:  ${fs_free_perc /media/EXTERNAL}%   ${fs_bar 6 /media/EXTERNAL}
sdc2:  ${fs_free_perc /media/usbdisk}%   ${fs_bar 6 /media/usbdisk}

the one in question is /media/EXTERNAL

here is the problem 

all my other HD's are monitored from 0 % to 100% meaning as i add stuff into them the number goes up.  All except the one i add today..it seems to be goin from 100% down..I notice when i was moving some stuff into it from other HD's and the monitor bar was normal...but the % said 99...98....97...basically counting down instead of up. i have included a pic of the assailant in question.
Now that i look @ it..all of them are goin down..how can i reverse the way they show hd usage to go from 0 to 100

[[IMG]http://img467.imageshack.us/img467/4201/screenshot3ui5.th.png[/IMG]](http://img467.imageshack.us/my.php?image=screenshot3ui5.png)

the one in question is SDC1 and SDC2 ( i make a small partition on the external for stuff a dvd burning storage folder.

---

### Post by m.musashi on 2007-03-03
I think you want to use this instead
```
${fs_used /media/EXTERNAL}%
```
When your drive is empty it is 100% free. When you add stuff it will have less free space so the percentage of free will go down. If you want it to increase as you add stuff you need to use the "used" percentage. When the drive is new, it is 0% used but as you add stuff the amount used will go up. I know it sounds kind of backwards but I think that's what you want.

---

### Post by kerry_s on 2007-03-03
If it's not counting down then your in trouble. Your using the free command, in other words % left from 100%. For instance your sdc1 says 76% that's how much space you have.

```
sdc1:: ${fs_used /} of ${fs_size /} = ${fs_free_perc /media/EXTERNAL}% ${fs_bar 6 /media/EXTERNAL} 
```

---


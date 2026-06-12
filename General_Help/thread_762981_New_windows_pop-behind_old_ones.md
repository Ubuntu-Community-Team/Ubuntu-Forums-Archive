---
title: "New windows pop-behind old ones"
date: 2008-04-22
forum: General Help
---

### Post by Lau_of_DK on 2008-04-22
Hey gents,

I have a problem with Ubuntu and its this: When I pop a new Window, either from the tray of a toolDialog (like the properties of a menu item) the new window will pop-behind all my other windows, forcing me to click the taskbar to view the window. 

Is this a bug? Can it be fixed?

Thanks in advance,
Lau

---

### Post by bingoUV on 2008-04-22
Are you using desktop effects?

---

### Post by Lau_of_DK on 2008-04-22
> **bingoUV said:**
> Are you using desktop effects?

Yes sir, Compiz fusion running at full speed. I just tried disabling it - then the problem disappears. Can this be fixed without disabling it?

---

### Post by bingoUV on 2008-04-22
Yes, I hope it can be fixed. In ccsm, set "General Options" -> "Focus and Raise" -> "Focus Prevention Windows"  to "any". 

Now close ccsm and open it again. Is the setting still "any"?

---

### Post by Lau_of_DK on 2008-04-23
> **bingoUV said:**
> Yes, I hope it can be fixed. In ccsm, set "General Options" -> "Focus and Raise" -> "Focus Prevention Windows"  to "any". 

Now close ccsm and open it again. Is the setting still "any"?

The setting was "any" to begin with. The others are as follows:

Clic to focus: on
Auto-raise: off
Delay: 500
Raise on click: on
Focus prevention: any.


I tried enabling auto-raise. It does not helps though.

---

### Post by erginemr on 2008-04-23
I am away from my Ubuntu right at the moment, but shouldn't you look for options to **disable** focus prevention? Is there any setting to turn if off there?

---

### Post by Lau_of_DK on 2008-04-23
> **erginemr said:**
> I am away from my Ubuntu right at the moment, but shouldn't you look for options to **disable** focus prevention? Is there any setting to turn if off there?

Well, even seperated from your Ubuntu your wisdom shines through: Youre right! I changed "any" to "none" which solved the problem ](*,)

To both you guys, thanks alot for your help.

/Lau

---

### Post by erginemr on 2008-04-23
Hi Lau,

Thanks, I am flattered. :oops:

Great news there. Take care... :D

---


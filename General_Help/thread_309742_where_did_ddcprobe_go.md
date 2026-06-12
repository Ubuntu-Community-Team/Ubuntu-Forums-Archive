---
title: "where did ddcprobe go?"
date: 2006-11-30
forum: General Help
---

### Post by Bubba Ho-Tep on 2006-11-30
Errrrr what happened to ddcprobe?

I've just installed Edgy on a brand spanking Core 2 and the screen resolution sucks. 

I've had this same issue with Hoary and Dapper on other boxen. My fix was $sudo ddcprobe to find my monitor's vertical and horziontal sync rates and then edited
/etc/X11/xorg.conf accordingly

badda bing done.

Except flaming ddcprobe isn't there in Edgy and it ain't in the repositories either. I did find something called xresprobe but it doesn't have a man page and google isn't helping much.

Anyone help me out?

---


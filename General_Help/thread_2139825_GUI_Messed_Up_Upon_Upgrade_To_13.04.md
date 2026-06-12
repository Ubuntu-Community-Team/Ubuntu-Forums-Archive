---
title: "GUI Messed Up Upon Upgrade To 13.04"
date: 2013-04-27
forum: General Help
---

### Post by JosephBeck on 2013-04-27
As you can see in the screen shot, circled in black, there is a weird box appearing in my dash and it is also present on the log out and shutdown screens. It's always in the bottom left corner. Anyone know how to get rid of that? I've also noticed when I right click pictures and then search for the program to open the image with, Pinta Image Editor doesn't come up as an option anymore even on the expanded list. What is up with that? I liked being able to use Pinta via right click instead of dash.




[IMG]http://i43.tinypic.com/p23v4.png[/IMG]

---

### Post by cprofitt on 2013-04-27
I am not having that issue...

Let's get some more details.
What is the make and model of your laptop?
What video card is in use?

---

### Post by mc4man on 2013-04-27
As far as your pinta issue - 
Open /usr/share/applications/pinta.desktop as root & add a %U the the Exec= line
see screen, line 165

---

### Post by JosephBeck on 2013-04-27
> **cprofitt said:**
> I am not having that issue...

Let's get some more details.
What is the make and model of your laptop?
What video card is in use?


Yeah it is weird, I've never had an issue before with Ubuntu. I upgraded directly from 12.10. I am using a HP Mini 210, a netbook. The graphics is saying it is an Intel® IGD x86/MMX/SSE2. Nothing fancy but it has worked perfectly fine before. I may just have to install from scratch or I have stumbled upon some random bug and will have to wait a week or so to get it fixed.

---

### Post by JosephBeck on 2013-04-27
> **mc4man said:**
> As far as your pinta issue - 
Open /usr/share/applications/pinta.desktop as root & add a %U the the Exec= line
see screen, line 165


Thank you very much, worked perfectly for the pinta issue.

---

### Post by mc4man on 2013-04-28
i'd probably  try switching the blur option to 'no blur', log out/in & see if it shows with no blur.
If not then switch back to active blur & see if any better.

The static blur option has issues & shouldn't be used. The no blur option generally is unsuitable unless you use a custom Background color  with some degree of opacity &  getting a custom color you like can be interesting, to say the least.
(Not an issue here as I use black as a custom Background color which works well with no blur

These options are best edited in ccsm (compizconfig-settings-manager) > unity shell plugin

---

### Post by JosephBeck on 2013-04-28
> **mc4man said:**
> i'd probably  try switching the blur option to 'no blur', log out/in & see if it shows with no blur.
If not then switch back to active blur & see if any better.

The static blur option has issues & shouldn't be used. The no blur option generally is unsuitable unless you use a custom Background color  with some degree of opacity &  getting a custom color you like can be interesting, to say the least.
(Not an issue here as I use black as a custom Background color which works well with no blur

These options are best edited in ccsm (compizconfig-settings-manager) > unity shell plugin


Didn't have to log out at all :) I had active blur and it seems to only happen when that is turned on, currently have it set to no blur. Not sure if I should report it as a bug or wait to see if it was just a freak accident. Thank you very much for the assistance. I'm not too excited about 13.04 so far. Hopefully it gets a little better as they go about fixing things over the next week or so. I really like unity which is the main reason I use Ubuntu but the group seems to be going in an odd direction. Software center and the update both now have "A" on them which to me is a subtle reference to Amazon which they are currently partnering with. Also not to hot about the splitting into two different update programs instead of keeping them together. Guess time will tell :O

---


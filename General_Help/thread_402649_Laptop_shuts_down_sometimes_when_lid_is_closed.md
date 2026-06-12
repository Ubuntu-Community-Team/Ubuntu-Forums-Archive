---
title: "Laptop shuts down sometimes when lid is closed"
date: 2007-04-06
forum: General Help
---

### Post by ahaurw01 on 2007-04-06
I've had a problem recently where my laptop (Dell latitude d810 running dapper) shuts down at (possibly) random times. It only happens when I have the lid shut on my laptop, but shutting the lid doesn't always guarantee that it will shutdown after some time. I usually experience this during the night and thought it was just a daily process that for some reason raised some terrible exception and just shut things down. But I combed through log files to find nothing surprising, thought it might be due to certain programs being left running, but none of that led me anywhere. I have also had it happen to me during the day when I shut the lid for a few hours, come back and it is powered down. 
My power settings go something like this:
 Running on AC: (which is when this always happens)
  - put display to sleep after 11 mins of inactivity
  - put computer to sleep when inactive for: Never.
  - when laptop lid is closed: Blank screen

 General: sleep type when inactive: do nothing
 same goes for sleep button action

Come to think of it, my display never goes to sleep anymore when it used to after the 11 minutes of inactivity.
I'm thinking now it's just something screwy with the power settings behaving rather strangely, but I really don't have any ideas beyond that.
I was planning on installing feisty after the 19th anyways, so hopefully that will fix things. Until then, does anybody have any clever ideas? Thanks for any comments
aaron

---

### Post by dmizer on 2007-04-06
laptops generally run at higher temps when the lid is shut, you could be getting a forced shutdown from the bios because of heat.  especially if the display doesn't completely shut off when you close the lid (ie, if only the backlight shuts off).

---

### Post by ahaurw01 on 2007-04-06
I see.. is there any way to force the display to shut off when the lid is down? This never happened to me running XP but the difference may have been that the display actually was turned off when I would close the lid in windows. Overall I don't think I have issues with overheating- it seems to run quieter and more efficient in dapper than it did in windows.

---

### Post by dmizer on 2007-04-10
courtesy bump.  not too sure how to answer your issue here, but i do have a laptop with a display that will not turn off completely, so it'd be nice to have an answer myself as well.

i'll try some digging on my and to see if i can't figure it out, but i don't have gobs of free time at the moment.

---

### Post by ahaurw01 on 2007-04-10
> **dmizer said:**
> courtesy bump.  not too sure how to answer your issue here, but i do have a laptop with a display that will not turn off completely, so it'd be nice to have an answer myself as well.

i'll try some digging on my and to see if i can't figure it out, but i don't have gobs of free time at the moment.

Thanks, dmizer. I installed feisty on a new partition just recently to see if doing so would fix my problem, thought starting fresh would make default settings definitely kick in. But no luck- it did it again last night. and I don't think that the display is ever fully turning off. Does anybody know what log files I can look into more carefully to find out exactly whats causing the shutdowns? Thanks again
aaron

---

### Post by joseftu on 2007-04-21
I'm having what sounds like the exact same problem on a Lenovo Thinkpad T43 running feisty.  I really don't think it's heat related.  That seems like a red herring to me, because lid open or lid closed this never happened on this machine with dapper or edgy.  For that matter, it doesn't happen with Windows, either--same machine.

---


---
title: "Firefox going absolutely crazy!!!"
date: 2008-06-19
forum: General Help
---

### Post by MongooseCage on 2008-06-19
Ok I have just updated my computer. There is a tip that asks me to restart firefox but it never goes away and my cpu wont reach below 80% when I have firefox on.

I think this is a conflict from a code i have typed in the terminal to get the youtube sound working.

I am not sure because I did it in haste but I think it was

```

sudo apt-get install libflashsupport

```

I dont believe that should have shaken it but whatsoever. My computer is slower than hell. Could anybody help me revert this?:confused:

---

### Post by Deutscher Alex on 2008-06-19
have you tried
```

sudo apt-get remove libflashsupport
```
?

---

### Post by MongooseCage on 2008-06-19
> **Deutscher Alex said:**
> have you tried
```

sudo apt-get remove libflashsupport
```
?

yeap! I also tried removing firefox and then reinstalling it. So now its pretty chilled out. After about five minutes the notification went. But it's back up now. Well somewhat, I dont know. It was quiet for a while and it jumped when I was about to post back and now again its calmed. It seems like it's an issue with the entire system. It tends to jerk off every minute or so for no reason.

---

### Post by Deutscher Alex on 2008-06-19
> **MongooseCage said:**
> It tends to jerk off every minute or so for no reason.

Hmm I'm pretty sure that's normal, cuz mine does the same thing... My cpu's hang out at around 50% each and the percentages jerk around a bit occasionally.

EDIT: Heh I closed firefox and 2 of my cpu's went down to 20% and the other 2 to 0%, so I guess that might not be normal.

Also, my cpu's only go up to 50% each on firefox 2.0.0.14; when i have Firefox 3.0 open by itself my cpu's go down to about 10% 

What version of Firefox are you using?


EDIT: Every time I opened my firefox 2.0.0.14 I had about 20 "phantom" windows open and disappear (through this glitch [http://ubuntuforums.org/showthread.php?t=833865](http://ubuntuforums.org/showthread.php?t=833865)). I managed to close all of the phantom windows except for 2 by closing them before they disappear, and my cpu's have calmed down to about 30% each. Do you happen to have that problem as well?

---

### Post by Deutscher Alex on 2008-06-20
alright I just had to retype this twice cuz the forums screwed up on me, so i'm gonna make this quick:

I stumbled upon this line that "sudo apt-get remove libflashsupport" spat out:
```
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libgtk1.2 libxml1 libgtk1.2-common
Use 'apt-get autoremove' to remove them.

```
After doing that autoremove, the %CPU usage of firefox 2.0.0.14 under "Processes" in the System Monitor halved to 16%... Still significantly higher than firefox 3.0's 4%, but it's something. So I suggest trying ```
sudo apt-get autoremove
```

---


---
title: "Avant Windows Navigator issue with Hardy"
date: 2008-05-05
forum: General Help
---

### Post by Mazen on 2008-05-05
i upgraded to Hardy, had a bit of trouble with the graphics, but now everything works perfectly with compiz and all except for AWN, which i can run but as soon as i click on anything the icons shift away from the bar as shown in the schreenshot.
Anyone had the same problem?or has a fix?
thanks

---

### Post by Cresho on 2008-05-05
you need to delay the launch of the avant navigator.

if you are a

create a file and call it avant.sh  then right click and on properties and then permission you allow for execute.

open the avant.sh with a text editor and paste this into it.

#!/bin/bash
sleep 10 && avant-window-navigator;

save and close.  NOW  in avant window navigator, remove the checkmark that allowes it to load at startup.  and in system->prefference->sessions, you need to  add avant and direct the command with the browse button to the sh file.  Now what this does is delays the launch of awn and launches most appropriatly.

---

### Post by prshah on 2008-05-05
> **Mazen said:**
> but as soon as i click on anything the icons shift away from the bar as shown in the schreenshot.
thanks

I had the same problem, also upgraded from Gutsy. The problem went away by itself after installing a bunch of updates (immediately after hardy upgrade completed).

---

### Post by moonbeam on 2008-05-05
> **Mazen said:**
> i upgraded to Hardy, had a bit of trouble with the graphics, but now everything works perfectly with compiz and all except for AWN, which i can run but as soon as i click on anything the icons shift away from the bar as shown in the schreenshot.
Anyone had the same problem?or has a fix?
thanks

There a fix posted in the following bug report:  [https://bugs.launchpad.net/awn/+bug/222300](https://bugs.launchpad.net/awn/+bug/222300)

Note that you will need to reconfigure awn afterwards.

---

### Post by burunji on 2008-05-05
Hi just unsinstall and install it again follow this links..


[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

it's very simple no bugs no nothing..it's working fine for me

---

### Post by Mazen on 2008-05-05
Thanks for the replies guys!
What i did was
 ```
gconftool-2 --recursive-unset /apps/avant-window-navigator

```
in the terminal, it reset everything and it works fine now!
i got it from [https://bugs.launchpad.net/awn/+bug/222300](https://bugs.launchpad.net/awn/+bug/222300) so thanks [moonbeam]("http://ubuntuforums.org/member.php?u=121213") 				:)

---


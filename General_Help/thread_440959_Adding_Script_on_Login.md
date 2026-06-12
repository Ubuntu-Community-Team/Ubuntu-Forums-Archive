---
title: "Adding Script on Login"
date: 2007-05-12
forum: General Help
---

### Post by Mudbream on 2007-05-12
Hi,

I'm on Feisty and I must be doing something wrong.
I'm trying to get Beryl to start on login using the Session manager GUI but everytime I add beryl-manager (or anything else for that matter) it looks like its added it correctly.
I click save session.
Close the GUI.
Open the GUI again and whatever I just tried to add is no longer in the Startup Programs list.

Is there something I'm doing wrong here?

Thanks,

Mudders

---

### Post by happyzax on 2007-05-13
Yeah, I had the same problem earlier tonight, but I got it working by doing this:

[INDENT][FONT="Courier New"] sudo chown -R username:usergroup /home/username/.config/[/FONT][/INDENT]

from the wiki page here:

[INDENT]_[https://wiki.ubuntu.com/BerylOnFeisty]("https://wiki.ubuntu.com/BerylOnFeisty")_[/INDENT]

Example:

If your username was 'joe'  then you would open a terminal window and execute this:

[INDENT][FONT="Courier New"] sudo chown -R joe:joe /home/joe/.config/[/FONT][/INDENT]

Hope this helps...

---

### Post by Mudbream on 2007-05-13
Thanks very much! That was the problem!
Works a treat now!

Thanks for the help!

---


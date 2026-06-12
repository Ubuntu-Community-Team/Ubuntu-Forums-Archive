---
title: "ReminderFox crash"
date: 2018-07-09
forum: General Help
---

### Post by lumaja2 on 2018-07-09
Ubuntu 16.04
 Reminderfox
 Thunderbird 52.8.0
 
 
 After trying printing all the reminders the screen went grey for a while and reminderfox dint show up I click on icon and again went grey then an window open with calendar on the left the title is
 ReminderFox [undefined] no reminders and the menu commands don’t work.
 How can I get this fixed?
 Thank you

---

### Post by Habitual on 2018-07-09
I'd try a re-install of ReminderFox (great utility FWIW)
also I'd try a [new profile for Thunderbird]("http://kb.mozillazine.org/Profile_Manager#Creating_a_new_profile") 52.8.0.
Fully exit and/or close Thunderbird and open a terminal then issue:

```
thunderbird --new-profile
``` Only problem w\that is, you'll need to re-setup your account(s).
Just 1 will be enough for this "test".

Also before that, you may wish to disable all addons except ReminderFox and see if another addon is contributing.

thunderbird 5 to 60.* is supported says [https://addons.mozilla.org/en-US/thunderbird/addon/reminderfox/versions/](https://addons.mozilla.org/en-US/thunderbird/addon/reminderfox/versions/)

Reminderfox version?
ReminderFox 2.1.6.3 is what I read at the site.

---


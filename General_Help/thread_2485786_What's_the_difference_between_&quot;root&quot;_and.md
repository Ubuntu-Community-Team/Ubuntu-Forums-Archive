---
title: "What's the difference between &quot;root&quot; and &quot;administrator&quot;?"
date: 2023-04-09
forum: General Help
---

### Post by ne29914 on 2023-04-09
In the PCManFM-Qt file manager, you can work with "root" privileges ("Tools" menu), which is extremely useful.
As of 22.04 LTS, there's a new option letting you work with "administrator" privileges.
So what's the difference?

Thanks.

---

### Post by mIk3_08 on 2023-04-09
> **ne29914 said:**
> In the PCManFM-Qt file manager, you can work with "root" privileges ("Tools" menu), which is extremely useful.
As of 22.04 LTS, there's a new option letting you work with "administrator" privileges.
So what's the difference?

Thanks.

In my opinion. In web based development. Administrator is working with  the GUI privileges (Backend) with limited only on some stuff while on root  privileges is working with all the main codes and the CLI (Cores "The  Hardcore in coding"). That's my opinion. Regards and cheers.

---

### Post by TheFu on 2023-04-10
[https://manual.lubuntu.me/stable/3/3.1/3.1.7/lxqt-sudo.html?highlight=administrator](https://manual.lubuntu.me/stable/3/3.1/3.1.7/lxqt-sudo.html?highlight=administrator)

---

### Post by ne29914 on 2023-04-10
Thanks TheFu, I read that myself, but it doesn't answer my question.
In my current installation (20.04), I have the option in PCManFM-Qt to open a new window with "root" privileges.
In 22.04, PCManFM-Qt has the _additional_ option of a new window with "administrator" privileges. This seems to do almost the same as "root", but not 100%. In fact, "root" works better, I've no use for the second option, so I wonder about its functionality.

---

### Post by TheFu on 2023-04-10
> **ne29914 said:**
> Thanks TheFu, I read that myself, but it doesn't answer my question.
In my current installation (20.04), I have the option in PCManFM-Qt to open a new window with "root" privileges.
In 22.04, PCManFM-Qt has the _additional_ option of a new window with "administrator" privileges. This seems to do almost the same as "root", but not 100%. In fact, "root" works better, I've no use for the second option, so I wonder about its functionality.

I didn't want to make up an answer.  If you really want to know, ask the Lubuntu team on their forums.  There was a feature request to make it easier to accomplish administrative tasks from the file manager. I didn't look any further.

---

### Post by ne29914 on 2023-04-10
OK, I'll leave it at that and keep using "Open as root" like before and ignore the "administrator" thing.
I just thought there might be an obvious explanation eluding me.
Thanks for the feedback.

---

### Post by MAFoElffen on 2023-04-10
Well, LOL.

root is a system account with full privileges over everything and can do anything it likes, rights and privileges wise.

An account that is a member of the wheel or sudoers group, by default is set to "ALL", but it "can be" set up as limited to just some admin privileges in the sudoers file. That way, say, a senior admin can give a junior admin certain rights, within turning them loose on everything without supervision. Or a database admin right to change things that affect the database.

I don't use Lubuntu a lot, except for testing other things... quiverc would be the person I know who would know the Lubuntu details and background.... If pcfileman made a change in their menu's from saying root to administrator, my guess is that it was just a change in verbiage.

---

### Post by ne29914 on 2023-04-10
Yep, that makes kind of sense, giving limited "root-like" options on a user basis. I'll buy that explanation :)

---


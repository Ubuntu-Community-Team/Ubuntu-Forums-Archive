---
title: "Upgraded to Hardy Heron and now number lock will not work"
date: 2008-04-27
forum: General Help
---

### Post by wolfpacker1983 on 2008-04-27
Hey guys,

I hust upgraded to Hardy Heron on my desktop and now the number lock keys on my 10 key pad will not work. I can turn the num lock on and off, but when it is on none of the number keys work. All the numbers on the main keyboard above the QWERTY keys work fine.

Has anyone else had this problem or know of a solution?

---

### Post by Skipster on 2008-04-27
I have the same problem.....

Hanent figured it out yet....

---

### Post by justinjstark on 2008-04-27
This has been discussed on the forums several times.

System -> Preferences -> Keyboard -> Mouse Keys
and uncheck "Allow to control the pointer using the keyboard"

Edit: Fixed.  Thanks Tarvok.

---

### Post by Skipster on 2008-04-27
Hmmmm  so simple....  yet so elusive....

That fixed it for me...  Thanks!

---

### Post by Tarvok on 2008-04-29
For anyone who is confused by this solution not being *quite* correct, the actual solution is

System -> Preferences -> Keyboard -> Mouse Keys

*Slightly* wrong option in the earlier post.

---

### Post by Butthead on 2008-04-30
Things must be different in Kubuntu "Hardy" LTS x64 then.

I don't see any "mouse keys" checkbox anywhere in there. :confused:

---

### Post by Jordinho on 2008-05-09
That check box doesn't even vaguely refer to enabling the keypad. How are users supposed to know this stuff. When is Linux going to get some sense?

---

### Post by justinjstark on 2008-05-10
> **Jordinho said:**
> That check box doesn't even vaguely refer to enabling the keypad. How are users supposed to know this stuff. When is Linux going to get some sense?

Ummm, it does because the keypad is what controls the mouse pointer when that option is enabled.  And it is off by default so it's not really a problem.  The problem is that when you upgrade from Gutsy, there is a bug of some sort that enables it.

---

### Post by F0EHammer_dg on 2008-05-14
> **Jordinho said:**
> That check box doesn't even vaguely refer to enabling the keypad. How are users supposed to know this stuff. When is Linux going to get some sense?

Yeah... I wish that Linux kernel would stop writing configuration dialog boxes.... when is Linux ever going to get some sense?  /sarcasm

---

### Post by PBK on 2008-05-19
> **justinjstark said:**
> Ummm, it does because the keypad is what controls the mouse pointer when that option is enabled.  And it is off by default so it's not really a problem.  The problem is that when you upgrade from Gutsy, there is a bug of some sort that enables it.

  I had this problem (Thanks for the fix), but I didn't upgrade from Gusty. I did a fresh install... ?? Main account had the problem, second "regular", non-administrative account did not have the problem.

Thanks for the fix, though...

---

### Post by Xyem on 2008-07-12
I experienced this problem with a fresh install of 8.04.

It only manifested after I had played on a game ( Rune to be precise ).

Perhaps there is a shortcut ( like the ones you always turn off in Windows :P ) that you can inadvertently trigger?

---

### Post by mlalkaka on 2008-07-13
This fix worked for me too. But I did a fresh install of Hardy Heron, and it used to work after the fresh install for quite a while. I only noticed it last week, so maybe it was a package update the caused the bug?

---


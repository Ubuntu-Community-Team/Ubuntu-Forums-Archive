---
title: "Keep programs running after i log out"
date: 2013-09-23
forum: General Help
---

### Post by geirmash on 2013-09-23
Hi! Is there a way to keep your programs running after i log out of the current user?
I am thinking like in Windows, when you log out.. and log back in, all your programs are still open.

Is there a reason why linux/ubuntu have not this enabled? -Maby security reasons?

---

### Post by Kirboosy on 2013-09-23
I'm assuming you are using Unity. Open up the "dconf editor" then navigate to **org**-->**gnome**-->**gnome-session**. Then click check the **auto-save-session** option. Close the window and that should do the trick!

Hope that helps!
~Caboose

EDIT: Thinking about it. That won't keep your programs running persay but reopen the applications that were running prior to logging out. 

I believe if you switch users using the user switcher (Guest session, etc.) that will give you the desired result. Also the alternative would be just lock the screen when leaving the computer.

[ATTACH=CONFIG]246453[/ATTACH]

---

### Post by ajgreeny on 2013-09-23
Do you actually want them to keep running, or just restart when you login again?

---

### Post by santosh83 on 2013-09-23
> **geirmash said:**
> Hi! Is there a way to keep your programs running after i log out of the current user?
I am thinking like in Windows, when you log out.. and log back in, all your programs are still open.

Is there a reason why linux/ubuntu have not this enabled? -Maby security reasons?

If you want to preserve the state of running applications (as opposed to just restarting them when you login again), I think on Linux hibernation might be the most trouble free way for you, provided your system hardware supports it. Hibernation (like the same thing in Windows) restores the entire system to exactly the state it was in when you invoked it, including the state of various daemons and servers. I think only the kernel is started as a fresh instance.

---

### Post by Habitual on 2013-09-23
> **geirmash said:**
> I am thinking like in Windows, when you log out.. and log back in, all your programs are still open.

Is there a reason why linux/ubuntu have not this enabled? -Maby security reasons?
Maybe because Linux isn't Windows? ;)

In 13 years of supporting Windows, I never saw that behavior ***except*** when using RDP or similar.

---

### Post by Kirboosy on 2013-09-26
> **Habitual said:**
> In 13 years of supporting Windows, I never saw that behavior ***except*** when using RDP or similar.

I believe he is refering to the "[Fast User Switching]("http://support.microsoft.com/kb/279765")" that can be found in Windows.

Anyways, geirmash were you able to find your answer?

~Caboose

---


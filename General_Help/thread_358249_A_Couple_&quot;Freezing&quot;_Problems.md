---
title: "A Couple &quot;Freezing&quot; Problems"
date: 2007-02-10
forum: General Help
---

### Post by Thrashers7989 on 2007-02-10
Hey yall.

I'm having two prevalent problems with my Ubuntu system. I'm running Ubuntu Edgy on an x86 system.

Problem one: laptop touchpad mouse freezes on "switch user"
Self explanatory. I'm using Ubuntu on my laptop and every time I select switch user, my touchpad mouse stops working on the login screen and the next user I log into. The touchpad will work again when I log back in

Scenario:
User A: touchpad working
User A selects switch user
Login Screen: touchpad no longer working
Log in to User B
User B: touchpad still not working
User B selects "log out" OR "switch user"
Login Screen: touchpad still not working
Log in to User A
User A: touchpad working again

If I log out instead of switch user, the touchpad will work just fine. While my touchpad is not working, I can still plug in my USB mouse and it will work perfectly fine, but the touchpad still will not.



Problem 2: Ubuntu freezes entirely if I don't immediately enter a password for my firewall.
I am using Firestarter Firewall and I have it set so it boots up with my system. Gnome (not the program) will ask for my password to turn on the firewall. However, if I don't enter this password immediately, the entire Ubuntu system will freeze and the ONLY way to get around it is to hold down the power button. I'm not exactly sure what's going on with that, but being a multi-tasker, I can't sit and watch my computer boot up and wait for this password screen, but I don't know if there's a way around this.



If you guys have any ideas, that would be awesome.

Bryan

---

### Post by MikeDX on 2007-02-13
I'm having the same trouble here on a latitude d400 laptop.

When switching users, we have one or all of these problems occur

the first user logged in will have their screensaver activate and cause X to default back to the first logged in user

the touchpad and buttons with crash but the nipple and other buttons will still work

the permissions of the users doesnt seem to matter either so it is very strange. i'd love to hear of a fix or workaround for it.

---

### Post by vanlue on 2007-02-22
I don't have a solution either, but I have the same user-switching problem on an HP Pavillion z5000 (64-bit) and an IBM ThinkPad T23 (32-bit).

Unfortunately it's not me that does the switching most of the time it freezes so I've had trouble getting information on exactly what causes it, but basically it happens when anyone tries to switch users instead of logging off one and logging the other back on.

---

### Post by MikeDX on 2007-02-24
I think I have the solution folks

If you install qsynaptics touchpad driver, and then remove the default x driver in xorg.conf, the touchpad and nipple both work regardless of login/out :)

Well, it works for the touchpad anyways....

---


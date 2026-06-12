---
title: "login problem - where to start?"
date: 2008-04-22
forum: General Help
---

### Post by scradock on 2008-04-22
Hi all - I have a nasty little log-in problem. When I attempt to log-in (Hardy 64-bit up-to-date, ie essentially RC) the screen goes blank ubuntu brown and never switches to my desktop. No panels, no icons, so I have no access to programs. Start-up programs start and show up, but nothing else.

Solution so far is to Change Session during log-in to Failsafe GNOME, which gives me the warning box and then starts up normally (!?) - with desktop, panels and all the bells and whistles. 

But I can't find out which start-up script got messed up, which config file needs to be mended, to return to normal behavior. Failsafe GNOME won't "stick" - I can't simply log in again, even though the session option says "As last login" - it reverts to the stuck mode, unless I select Failsafe GNOME again during log-in.

I've looked around in the gdm scripts, but haven't managed to find what needs fixing. Any ideas? Anyone else been in this particular hole?

---

### Post by bingoUV on 2008-04-23
I guess you are carrying forward an earlier home directory. Try creating a new user, and see if you can login normally with it.
One by one, try copying the following to the new user (or taking out of the current user, backup somewhere else).
1. .xsession
2. .bashrc
3. directories inside .gnome2
4. .dmrc
5. .gconf
there might be more, but so much for now.

Check when this progressive removal enables you to login normally.

---

### Post by scradock on 2008-04-23
Thanks for the suggestions. I've tried creating a new user - the new user logs in normally, but with a plain vanilla desktop. That's a start!

I don't have a file .xsession in /home/olduser or /home/newuser. Is it somewhere else?

Shifting the olduser versions of .dmrc and .bashrc into the newuser home folder doesn't break the login, so it's probably not either of them that is messed up.

Both .gnome2 and .gconf are great stacks of nested folders; the problem probably lies in one of them, as you suggest, but I'm not sure how to find out just where. I will try moving some parts around and see what happens.

I'll report any progress!

---

### Post by bingoUV on 2008-04-23
Ubuntu does not create .xsession by default. It is no problem if it does not exist.

---

### Post by scradock on 2008-04-23
OK, that's not a problem.

I tried switching the .gconf folders en masse - using the newuser .gconf allows the olduser to login OK, but with the vanilla desktop, and lots of other settings will have changed along with that.

Unfortunately, either I did something wrong, or simply re-naming .gconf to .gconf.bak wasn't acceptable - now it has vanished, and I don't suppose I shall ever see it again. So I'll have to re-configure everything to get it the way I like it.

But I can now login, which is a great step forward! Thanks for the help.....

---

### Post by scradock on 2008-04-23
OK, the last post is wrong on several counts - I was too tired to be doing tricky stuff last night!

First, yes, making a new user showed that the system worked OK, but without all the customizations.

Second, shifting .gconf actually made no difference - the old user still got the log-in failure even with the .gconf from the newuser. 

Thirdly, I didn't lose the old .gconf, so I just swapped them back again and tried some more possibilities.

FINALLY, I looked in .gnome2, as suggested, and saw a file called "session". I tried changing its name and rebooted, with no problem logging in. So that's it - there was something wrong in the .gnome2/session file, and it just needed to be thrown out and the system recovered its ability to reboot correctly.

Hope that helps someone else in a similar sticky place..... thanks for the help.

---


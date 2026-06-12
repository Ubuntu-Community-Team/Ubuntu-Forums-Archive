---
title: "Gutsy upgrade issues: users admin not showing users, emerald not showing themes"
date: 2007-10-07
forum: General Help
---

### Post by vav on 2007-10-07
I upgraded to Gutsy and compiz fusion works very well on my 2 year old non-gaming machine! Fun times...

However, I was trying to install Virtualbox which needs tinkering with users and groups. I fired up users-admin, but it doesnt show ANY users! Then I clicked on Manage groups and that's blank too! I got around the issue using usermod in a terminal, but I need my users-admin to work :P

Another possibly unrelated issue: I installed emerald manually through synaptic to change the window decoration, it works and defaults to a red border which is ok, but if I open 'Emerald Theme Manager' from System->Preferences, it doesnt show any themes! I even tried to use the Fetch GPL'd/non GPL'd themes etc buttons after installing svn and whatnot. (That's when the window border changed to the default red). How to fix this?

Lastly, my bottom panel seems to disappear every once in a while, especially after suspend/wake up when I have to restart emerald...

Please advise...

---

### Post by phazei on 2007-10-08
I had the same issue with the no users listed in the users and groups window.

I installed Gutsy beta 2 days ago.  After the install was finished I changed a bunch of stuff and then I went to create a new user  so i'd have a backup privileged acct in before I screwed my main account while messing with it.  So I created account admin2.  But I didn't see anything listed.  I decided to try it so I switched users and tried to log back in.  admin2 didn't work.  So i logged in with the admin account, and it had desktop user privileges!!!
I typed users in terminal and it shows admin as logged in twice!!  So I had no more admin privileges, and my admin2 acct wasn't created.  I rebooted and when it was trying to load, it said Gnome Display Manager, user gdm not found and had me login at the cli !!

So I reinstalled off the live dvd and I created the new users first thing after install.  It listed the main account and the root account there that time.  It's worked fine since.  I just wrote it off as a glitch.

And I have the same problem with emerald, I'm working on getting fiestys emerald-themes package right now.

---


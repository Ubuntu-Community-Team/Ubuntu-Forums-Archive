---
title: "Why is my computer impossible to turn off with multiple users?"
date: 2020-07-06
forum: General Help
---

### Post by anonymouscoward2 on 2020-07-06
[UBUNTU]

My account is the first and administrative account.  I have set it with two other family members as users so we don't mix and match files.  I set it last month to go on standby if I press the power button (but that's gone from the Settings->Power since the last update).  I found that was broken once I added multiple users and they logged on, even if they had the same setting set.

When I try to poweroff via the screen (upper right) it's either nonresponsive or says these users are still on.  I get that they might have left their browser running and haven't properly logged off, but I think "Switch User" should log them off.  They don't have my password and I don't have theirs -- so I'm finding it impossible to log into their account to log them off, I mean what a ridiculous concept even.

Is there a fix?

---

### Post by Doug S on 2020-07-06
This will work:

```
sudo shutdown -h now
```

You can also specify a delay and a message to logged on users, if you want. See the man pages.

---

### Post by anonymouscoward2 on 2020-07-06
I tried pkilling other users from the admin account but for some reason it logged me off and then when I logged back in my screen was scrambled until the next forced restart.

The shutdown command works okay, but honestly, I was hoping I could get the power button to work flawlessly to go to standby.... because my relatives are still less than computer savvy.  I still have to show them how to move files (pictures) around in a folder hierarchy that's GUI-based and they've been using computers for 12 years.  So yeah, I don't think terminal commands are going to be their thing.

Oh well, it's kinda annoying having this old computer run sometimes 12h a day on the electric bill.  90% unused.

Is there a script or something I can run that checks every two hours with a popup box and if no ones there runs the shutdown command?  For all users?  That I can live with.

---

### Post by Impavidus on 2020-07-06
"Switch user" allows a new user to log in without logging the previous user out. The session of the previous user stays locked and can be resumed later, when the second user has logged out. It can be useful if you want to give another user quick access for a few minutes, then resume work for the first user. If you want somebody to log out, use logout. So tell people that when they stop using the computer, they should click "log out", not "switch user".

---

### Post by anonymouscoward2 on 2020-07-07
Okay, so just for absolute clarity there is no master switch I can use to have the computer go to sleep automatically when idle, no matter the account, when I'm not there to babysit the computer?

---


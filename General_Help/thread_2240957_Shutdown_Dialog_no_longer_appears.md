---
title: "Shutdown Dialog no longer appears"
date: 2014-08-23
forum: General Help
---

### Post by Dennis N on 2014-08-23
I have suddenly lost the shutdown dialog in Xubuntu 14.04 that appears when you use the Log Out... action button on the right end of panel (see first attached image which shows my settings). This is the dialog that offered Log Out, Restart, Shut Down, or Suspend. Now instead of the dialog, I go to the login screen instead. The same is true if I use the Log Out... at the top of the Whisker Menu.

From the guest session, the dialog appears as it should.

Executing **xfce4-session-logout** in the terminal also takes me to the login screen instead of the shutdown dialog. I do get the shutdown dialog if I execute this command from the guest account (see second attached image), so something has gone wrong with my configuration. 

How can I restore the shutdown dialog? I can't figure it out. Thanks.

---

### Post by Toz on 2014-08-23
Do you have Settings Manager >> Session and startup >> General tab, "Prompt on Logout" checked? It needs to be checked if you want to be prompted with that dialog.

---

### Post by Dennis N on 2014-08-23
Well, that did it. Didn't know that was needed to show the dialog. I did uncheck it to remove prompts on the restart and shutdown without realizing the "side effect" of no option dialog at all for Log Out...

Now it's checked again, as I like the all in one dialog. Thanks for your advice and saving me a lot of time.

---


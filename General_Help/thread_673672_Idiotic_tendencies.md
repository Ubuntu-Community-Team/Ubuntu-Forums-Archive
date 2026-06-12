---
title: "Idiotic tendencies"
date: 2008-01-20
forum: General Help
---

### Post by kaufmannn on 2008-01-20
I have yet again proven that I can be quite idiotic, as I "broke" Ubuntu. I'll start at the beginning so there is at least some logic into my intentions, not so much in the execution. 

I am running Ubuntu 7.10 64-bit on a Wubi install, dual booting with Vista on a Toshiba A100-TA7 laptop - just to get that info out of the way, though I doubt that will really come into play. 

I originally had my login set to prompt for user name and password, but I changed that to autologin not too long ago. I'm not sure if I started getting a prompt for a password to allow keyring access to that nm thingy right away, but eventually they appeared and quickly became annoying. 

I became fed-up with this earlier today and searched the net (not here, foolishly) for a fix (googled "default keyring unlock"). This is what I found to do, appended the following to the end of /etc/pam.d/gdm:

```
@include common-pamkeyring
``` 

In fact, I also inserted that into /etc/pam.d/gdm-autologin (or something to that effect). In hindsight, I should have listened to my subconscious, I had a feeling that the "fix" was for pre-feisty releases, so gusty definitely would not have needed it, and I did not see common-pamkeyring in the /etc/pam.d folder. 

But I thought "hey, worst that could happen is I have to undo what I did because my internet no longer works." Yeah... I cannot even log into Ubuntu, I am brought to the GDM and am face to face with some error that I cannot get rid of, no matter how many times I click the only button available (either ok or cancel, I forget... not that it matters). 

I went into Ubuntu "safe mode" hopeing maybe it would fix it, but no such luck in the end I get to the GDM dead end. Well, actually I do have the option to go into a root prompt before the GDM, but I would have no idea what to do from there.

I did not save a copy of the original under a different name, because what I did was so simple I thought I could fix it easily just by going back into the two files and removing the line of code.

Do I need to reinstall? Or is there hope?

---

### Post by glotz on 2008-01-20
Perhaps this will work.

Drop to the terminal. Type in sudo nano /etc/pam.d/gdm and remove the line. Hit Ctrl+X to exit and save the file (with the same filename!) Repeat for whatever files you changed. Restart.

---

### Post by kaufmannn on 2008-01-20
I'll try that asap, thanks. I'm just perusing the interwebs right now to learn some basic terminal commands... should have done so awhile ago. Oddly, this is how I learn computers. I think I know what I'm doing, mess stuff up and then have to find out how to fix it, learning more in the process.

---

### Post by glotz on 2008-01-20
That's probably the best and the only way! :)

---

### Post by kaufmannn on 2008-01-20
And it worked! Back into my comfortably customized Ubuntu... much better. 

Another question, do you know how to fix that nm-applet problem I'm having or could you direct me to a solution where I won't mess things up again? 

Though I now know how to fix such mistakes (is that good or bad? Such events may become more frequent now).

---

### Post by glotz on 2008-01-20
No idea about it. Keep on hacking!

---


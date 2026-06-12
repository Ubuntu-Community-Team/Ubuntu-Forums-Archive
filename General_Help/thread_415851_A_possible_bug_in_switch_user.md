---
title: "A possible bug in switch user"
date: 2007-04-20
forum: General Help
---

### Post by Jay_Dogg on 2007-04-20
Hello, I need your help in determining whether the following issue is a bug or just my problem. In any case, it's quite crippling to me. I've got a clean Feisty and Edgy and Dapper didn't have this problem.

You need user accounts A and B to do this.

1. Login with user account A
2. Lock the screen and switch user
3. Login with user account B
4. Lock the screen again and then open the lock(don't switch user)
5. Logout user B and BOOM! (My computer freezes completely)

I'm not the only one that uses this computer so switching users is essential and this doesn't help at all

---

### Post by Jay_Dogg on 2007-04-21
Anyone?

Edit: Disabling screensaver from other accounts seems to remove the problem as their screens aren't locked anymore... Anyway is this my problem only?

---

### Post by shinythings on 2007-04-21
I have this problem too, it can be rather annoying. The only thing I can do is alt-print-S, alt-print-U, alt-print-B to restart the computer. 

Btw, I have an Asus laptop with an ATI Mobility Radeon X700 and am using the radeon (not fglrx) drivers.

Has anyone else encountered this?

---

### Post by Jay_Dogg on 2007-04-21
Yes, the open source Ati drivers are the cause, I think. I changed to "vesa" in xorg.conf and now it works fine, but with "ati" these crashes occur.

Edit: I have Radeon X800 Pro

---

### Post by hashimoto on 2007-04-21
There is definitely something wrong with the Switch User function. My wife was logged in and I used the Switch User. The login window resolution was 800x600 and so was my desktop. I wasnt even able to select a bigger resolution as the alternatives had disappeared. This does  not happen if I log her out and then log in to my account.

And I have a NVidia card & driver.

---

### Post by kseise on 2007-04-30
I have the same problem, but only on Feisty.  My wife tried to log in (switch user) and the screen went black.  Nothing came back up.  Alt + CTL + F1 didn't take me to the rescue command line.  I had to actually use the reset button on the box to reboot the machine.

---

### Post by EmmAytch on 2007-06-06
I have the same problem.  A clean install of Feisty and it is the user A, user B scenario, where you switch users then try to log one of them out.  Switching back works - but of course will always lead to someone's account being left open as the PC shuts down.

Last week we had the latest kernel update plus a load of other stuff - and it fixed it.  Then we got some more updates a few days later - and it's broken again.

I think there was an xorg update in there somewhere, but I can't remember.  Thing is, it is now not fixed whereas 3 days earlier it was!

---


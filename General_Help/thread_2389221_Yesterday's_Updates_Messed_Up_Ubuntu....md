---
title: "Yesterday's Updates Messed Up Ubuntu..."
date: 2018-04-13
forum: General Help
---

### Post by tb75252 on 2018-04-13
I use Ubuntu 16.04 LTS, 64-bit.
Yesterday evening some updates got installed.  Since then, I am unable to use Ubuntu.
When I boot up my PC I can log in into Ubuntu but after the login screen all I see is a fuchsia-colored screen and the wording "16.04 LTS" in the lower left corner.  All my icons on the left side of the screen are gone and even the menu bar on top is not accessible.
Do I have to resort to re-installing Ubuntu to fix the problem?

---

### Post by dragonfly41 on 2018-04-13
Just as a long shot (since I see this effect every time I boot up and don't yet have a permanent fix) ...

Check to see if your mouse arrow disappears off edge of screen.

If so, you might have dual monitors and your content is "off screen" ...

Type [Super key]+[P key] to try switching displays.

When you are back to your desktop run command **arandr** to setup displays.

---

### Post by tb75252 on 2018-04-13
> **dragonfly41 said:**
> Just as a long shot (since I see this effect every time I boot up and don't yet have a permanent fix) ...

Check to see if your mouse arrow disappears off edge of screen.

If so, you might have dual monitors and your content is "off screen" ...

Type [Super key]+[P key] to try switching displays.

When you are back to your desktop run command **arandr** to setup displays.
Thanks for the reply.  I'll try your suggestion this evening when I go home from work.
With "Super key" you mean the Windows key, right?

---

### Post by dragonfly41 on 2018-04-13
Right.

---

### Post by Yellow Pasque on 2018-04-13
Have you tried creating another user to see if the problem exists there?

---

### Post by dragonfly41 on 2018-04-13
My own particular dual-screen glitch is seen even before I log in with password after booting up.
I have to toggle [Super key] + [P key] after booting to see the login. And again to see Desktop.

The OP might try creating another user as suggested. 

I can live with this since soon I'll be switching to 18.04, But it would be nice to pin down the cause.

[Lateredit]
Actually tried Guest login session after reboot and have same pseudo dual monitor symptoms.

---

### Post by tb75252 on 2018-04-14
Started up my PC on Saturday morning and Ubuntu loaded without a glitch.  So my screen now looks normal.  Don't know what the deal was on the previous day.  I have the feeling that maybe my HD was not spinning after the login screen but now everything looks ok.

---


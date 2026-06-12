---
title: "[SOLVED] Dimmed Screen Does Not Brighten After Entering Password"
date: 2008-05-03
forum: General Help
---

### Post by alsamman on 2008-05-03
I'm not sure if this is only a problem with me, I think it is most likely a Hardy bug. As you all know when you access anything from System>Administration, the screen dims and you have to enter your password to proceed. Once you enter password, the screen brightness goes back to normal. The problem that I am having is that after I enter my password, my screen does not brighten back up like it should.

This part I am going to explain will probably confuse some people because it's hard to describe, if you don't understand that just forget this part
-> When I am on the desktop and I highlight, any part of the screen that gets under the highlight box will bring the brightness back to normal.

---

### Post by alsamman on 2008-05-03
bump

---

### Post by ddrichardson on 2008-05-03
I think its a bug - my laptop does it too. If the screen brightness is controlled by a command then it could be added to the resume scripts.

---

### Post by Erebus.Thanatos on 2008-06-16
I had the same odd problem.   It dimmed on me and would not go back to normal even after a restart.  The only fix i had was to go back to the power management setting and turn off both dim settings System -> Screensaver -> Power Management.  After i unchecked the two Dim buttons (Both on AC power and on Battery Power) I had to unplug and plug in my power cord until the screen returned to normal.  Probably a bug in Hardy.

---

### Post by tomstrummer on 2008-06-18
Same problem -- If I understand you correctly this is *not* a power management problem, right?  This is when gksudo dims the backgound to put visual focus on the "enter your password" dialog.  Once you enter the password, the dialog closes but that translucent overlay is still painted on the rest of the screen. Right?

This started when I upgraded to Hardy.  I've noticed that if you take a window and drag it around the screen, it "wipes away" the overlay.  Or if you switch virtual desktops it goes away.

AMD64, Dual Monitors w/ NVidia something card.  Anyone else?

---

### Post by hoangtk on 2011-05-03
Me too, I am using Vaio VPCF111Fx with Nvidia 310M & Ubuntu 11.04. When computer is idle, the screen dims. Then it does not brighten at all. I even can not see the unlock screen. After managing to enter password and login, it still dim. Adjust brightness using Fn+ ... is useless.

---

### Post by fleurink on 2012-01-06
Same here: screen brightness will not go back no normal when activated after dimming. I can hardly see the login screen, but it's there. Screen with normal brightness will come up though after closing and re-opening the laptop. 

Using Ubuntu 11.10 on Compaq mini 110.

---

### Post by coffeecat on 2012-01-06
Old thread which dates back to 8.04 days. Closed.

Screen brightness and dimming function varies between different makes and models of laptops. Please start your own threads if you need help with this.

---


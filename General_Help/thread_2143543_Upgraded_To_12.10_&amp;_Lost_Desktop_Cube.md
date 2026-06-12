---
title: "Upgraded To 12.10 &amp; Lost Desktop Cube"
date: 2013-05-09
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-05-09
Hello,

I just upgraded to 12.10 and lost the Desktop Cube. Also CCSM was removed.  I also remember being asked whether to select GDM or LiteDM and I chose LiteDM because it was the default setting.  Should I have chosen GDM instead; and is it possible to get it back if necessary?  Is it even possible to have the Desktop Cube in 12.10?

Thanks Hannibal

---

### Post by kanikilu on 2013-05-09
Difference between GDM and LightDM shouldn't matter. Just reinstall CCSM, if necessary, and enable the Rotate Cube plugin. I have it working on my 13.04 desktop which has been in-place upgraded from 12.04 to 12.10 to current.

---

### Post by coljohnhannibalsmith on 2013-05-09
I can't find the rotate cube plugin.  Where do I look?

---

### Post by watgrad on 2013-05-09
I think you will have to enable additional animations using synaptic.
Install synaptic package manager.
Search in synaptic for compiz.
Find and install the compiz-plugins-extra package.

---

### Post by coljohnhannibalsmith on 2013-05-09
OK I've got it all setup, but; the cube will only rotate when I press ctl-alt and drag the mouse.  It won't rotate when I click on the desktops in the lower right hand corner.  Also, the desktop icons don't appear on any other workspace.

Thanks Hannibal

---

### Post by mc4man on 2013-05-09
> **coljohnhannibalsmith said:**
> OK I've got it all setup, but; the cube will only rotate when I press ctl-alt and drag the mouse.  It won't rotate when I click on the desktops in the lower right hand corner. 

Thanks Hannibal
try setting ( or unsetting & resetting ) in rotate plugin > Bindings > Rotate Left > enable & pick bottom right corner, noting that here on a laptop it only works with a usb mouse l. click, not a touchpad l. click
(Rotate right can only be set to upper left corner unless you hide the launcher or get rid of the trash icon. The launcher is a bit of a blocker also for dragging windows to left > next WS, it can be set & works, then eventually breaks & needs resetting

Overall unity/compiz remains a bit of a mess & always will be a mess until it's gone

Edit: it would appear that the binding is lost on a log out/in but on a restart/fresh boot come back, certainly a bug, likely never to be fixed in Ubuntu

---

### Post by coljohnhannibalsmith on 2013-05-09
> **mc4man said:**
> try setting ( or unsetting & resetting ) in rotate plugin > Bindings > Rotate Left > enable & pick bottom right corner, noting that here on a laptop it only works with a usb mouse l. click, not a touchpad l. click
(Rotate right can only be set to upper left corner unless you hide the launcher or get rid of the trash icon. The launcher is a bit of a blocker also for dragging windows to left > next WS, it can be set & works, then eventually breaks & needs resetting

Overall unity/compiz remains a bit of a mess & always will be a mess until it's gone

Edit: it would appear that the binding is lost on a log out/in or reboot so overall may be a waste of time pursuing..

The above didn't work.  Infact every icon on the screen dissapeared when I clicked one of the workspace icons; however ctl-alt left & right arrows worked perfectly.

Any onther suggestions helpful.

Thanks Hanninbal

---

### Post by mc4man on 2013-05-09
set up & try another user account if your install was the result of an upgrade.

Just noticed the corner flip  binding(s), when set will always work on a fresh start/reboot, never on a log out/in

---

### Post by coljohnhannibalsmith on 2013-05-09
I was able to create a user in User Accounts; but I was not asked for a password during creation and the account was disabled.

In the bottom right-hand corner of the screen is the Workspace Switcher.  What I'm trying to do is change some setting, so that when I click on a workspace on the workspace switcher, the cube will rotate to the selected workspace.

Also, when I try to change workspaces by pressing ctl-alt left or right arrow the cube rotates, but stays on the first workspace.  Also, when I press ctl-alt and drag the cursor with the touchpad, the cube rotates, but stays on the first work space.  I've searched the Internet for the proper settings for workspace switcher, but when I used the settings I was instructed to use, I still had the same problems.

Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2013-05-10
Hello,

I finally found the solution to both problems.  The Desktop Cube problem was caused by the Desktop Size settings.  At first I tried to set the Desktop Size at 4, 1, 4 and that didn't work.  Then I remembered I still had the original drive.  The Desktop Size settings on that were 4, 1, 1.  I tried this on the new drive that I recently upgraded and the Desktop Cube worked perfectly.

Then I found a way to create a new user account.  I had to click on a part of the window that didn't show itself as a button until I clicked there.  This allowed me to enter a password and enable the account.

Thanks Hannibal

---


---
title: "Software updater can't be opened or closed"
date: 2013-08-20
forum: General Help
---

### Post by Mazate on 2013-08-20
Hello

Whenever there are updates, the software updater appears in the Unity bar.  If I click it, nothing happens.  If I right click it, it gives me the option to install all updates, which it does.  But, nothing opens up to show me the progress of the updates.  It just happens in the background.  Then once the updates are installed, the installer icon still sits there and won't close unless I reboot.  If anyone knows why this keeps happening, I'm all ears.

---

### Post by ibjsb4 on 2013-08-20
Have you tried reinstalling update-manager and update-manager-core?

I did a quick bug search and didn't hit on anything.  You may want to dig around.

[https://bugs.launchpad.net/ubuntu/+source/update-manager](https://bugs.launchpad.net/ubuntu/+source/update-manager)

---

### Post by solitaire on 2013-10-04
I'm having the same problem!
it started in 13.04 and persisted when I upgraded to 13.10 a few days ago.

The notifier pops up on the side bar and if you select "Software Updater" from a right click on it nothing happens.
If I select "Install all updates" it updates in the background with no GUI being displayed.

If I close the notification on the side bar and I run "update-manager" from the terminal then things run fine (GUI opens and I can see and select what updates to run).

Is their anywhere in the logs to check things? it seems like the notification icon is not linked to the update program or at lest not linked to it's GUI...

---


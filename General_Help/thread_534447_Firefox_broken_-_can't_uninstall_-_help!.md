---
title: "Firefox broken - can't uninstall - help!"
date: 2007-08-25
forum: General Help
---

### Post by acl123 on 2007-08-25
Hi,
My firefox won't open anymore. When I run it, it opens a tab in the application panel that says "Starting Firefox Web Browser" but then disappears.

I went to synaptic packet manager and marked it for reinstallation but that didn't appear to do anything.

If I mark it for uninstallation it says it is going to uninstall ubuntu-desktop which I don't think would be a good idea at all!!

This is how the problem started:
I noticed that Google Browser Sync wasn't syncing my bookmarks at all. When I tried to edit the plugin's preference I noticed that none of the buttons in the setup window did anything. I then uninstalled Google Browser.
After I did this, Firefox wouldn't open until after three attempts.
I then installed Foxmarks. But when I was going through it's setup wizard I got a popup window saying "Setup:" with a button for Help and Cancel! How annoying.
So then I uninstalled Foxmarks.
And now I can't open Firefox at all!

This is the Ubuntu 7.04, Firefox 2.0.0.6.

I've only had Ubuntu for a week - how can it be ruined already like this?!

---

### Post by dragonwings on 2007-08-25
go to 
system
then
addministration
then
synaptic package manager

then search for
firefox

when you find it right click on it and mark it for reinstallation

---

### Post by acl123 on 2007-08-25
Hi, thanks, but I've tried this and the problem remains.

---

### Post by luisromangz on 2007-08-25
Removing ubuntu-desktop won't be as bad as it may sound, it's only a metapackage. If you remove it, no other package should get uninstalled, as no package depends on it. You can see that in synaptic, when marking firefox for uninstall, how many packages are marked for uninstall also?

ubuntu-desktop package is useful for example while performing dist-upgrades, as it depends on the default packages of Ubuntu, so you can be sure that you are performing a full upgrade and that you will get all the new programs included in the new version.

---

### Post by acl123 on 2007-08-25
Hi, thanks for that.
Ok I marked firefox for complete removal.
After that I rebooted my computer, then reinstalled firefox.
Firefox still won't start! This is horrible!

I noticed that after removing firefox there was still a lot of stuff in my home directory under ./mozilla/firefox/...   including an extensions folder. Could my extensions still be installed? If so, how can I get rid of them (I marked it for Complete Removal after all)?

---

### Post by acl123 on 2007-08-25
Ok I fixed the problem by deleting the .mozilla folder under my home/username directory.
What was that folder for?

Also, I noticed that I could run firefox if I typed "sudo firefox" in the command line.
But then if I just typed "sudo" I got the message "segmentation fault (core dumped)" and firefox wouldn't open.

It would be much appreciated if someone could explain what's just happened - it's very confusing, and very annoying because now I've lost all my firefox settings!

---


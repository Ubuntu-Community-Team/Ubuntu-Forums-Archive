---
title: "firefox with no flash crashes all the time!!! Help!!!"
date: 2008-03-02
forum: General Help
---

### Post by jesushero on 2008-03-02
Firefox has always been a big problem for me! I used to have adobe flash, it crashed all the time. I then proceeded to try various different flash plugins but it made no difference. I then decided to completely disable and uninstall flash. I did so and had no problems for about two weeks. Now it all started again with no flash!!! Firefox crashes approximately every 4 to 5 minutes for no apparent reason. It can be on google,com or on a flash site that can't be displayed. It will not last longer than 5 minutes. I can't seem to find any problem!!! So should I totally remove firefox?? I've been using lynx which I love but most of the sites I use for my work are not compatible with lynx. Lynx never crashes!! It has NEVER EVER crashed!!! Is there any browser that actually works or do I have to switch to windows or a different distribution of linux?? I'm sick and tired of firefox!! 

Any suggestions??

---

### Post by oakgrove on 2008-03-03
It could be some plugin you have that is causing it.  To start fresh, open your file manager and navigate to the /home/yourusername/.mozilla/firefox/ directory.  In this directory, you will see a folder ending in the word .default.  This is your default profile that contains all of your plugins, bookmarks, settings, etc.  You want to backup that folder by copying it to another folder.  Make sure you copy it and not just move it.  After you've done that, shut down firefox and go into your profile and delete its contents.  This will allow you to restart firefox with a clean slate that you can test and see if it is now stable.  If so, something in your profile was causing your woes.

You can always bring your old profile back by deleting the contents in your profile directory that firefox rebuilt after deleting the old stuff and copying your old profile back into it.

---


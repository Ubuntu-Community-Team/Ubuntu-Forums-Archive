---
title: "[Lubuntu] Advanced Noob user needs help."
date: 2018-10-06
forum: General Help
---

### Post by ynsano on 2018-10-06
First of all... i'm a Advanced user but i'm still learning the "moods change" of Linux World so.. I'm an Advanced Noob... so use tech lang at will... but expect me to be lost in one or another point....

Now my problem...
I was trying to make a program work and for such i had to install some QT library or something like that... now my lubuntu closes some programs automatically when it tries to use that "Visual windows build" i mean some programs were using that simple light gray theme that Lubuntu uses.... now they try to load a black elaborated one... but they crash and closes right after opening... now i need help to either.. eliminate the packages that made this... or to complete the install to make lubuntu fully support that... now comes the big problem... i cant remember the names of the packs... i only remember it had something do to with the QT...

---

### Post by TheFu on 2018-10-06
A common troubleshooting technique is the create a new userid, login under that user and see if the problem persists.  If it does, then it is a system-wide issue.  If it doesnt, then it is only for that single userid and probably some corrupt config file in the HOME.

The description doesnt help me. Im not a Qt expert.

---

### Post by ynsano on 2018-10-08
I did the another user test.... same results.... i'm posting a screenshot of the style on the left is the normal Lubuntu one... on the right... qBittorrent that was gray too... until something in qt made it black like that... and closing all the time when it tries do draw something on the window....

                                        [ATTACH=CONFIG]281279[/ATTACH]

---

### Post by oldos2er on 2018-10-08
Moved to General Help since Lubuntu is an officially supported "flavor".

---

### Post by TheFu on 2018-10-08
> **ynsano said:**
> I did the another user test.... same results.... i'm posting a screenshot of the style on the left is the normal Lubuntu one... on the right... qBittorrent that was gray too... until something in qt made it black like that... and closing all the time when it tries do draw something on the window....

                                        [ATTACH=CONFIG]281279[/ATTACH]

Can you restore from a backup prior to the problem?  Then take careful notes for anything you do going forward?

If not, and if you need the system working today, I'd wipe everything and reinstall Lubuntu. Takes 15min.  Of course, backup any data you want or just backup the HOME, since that doesn't seem to be the issue.

If the issue is only with the bittorrent thing, might try purging that cleaning up any settings, then reinstalling just that package.  If it is all Qt programs that seem to have switched to a dark theme, and you have both a little time and already backed up everything you want to keep, then maybe installing kde-desktop, logout, login (choosing KDE for the DE) and selecting a lighter theme?

Just providing options.  I haven't any clue about this at all, really.

---

### Post by Claus7 on 2018-10-11
Hello,

in lubuntu the theme settings are changed under: lubuntu options (icon in the panel bar)->Preferences->Customize Look and Feel

Have you tried to change anything from there? You have the options to change widget and color among others. Maybe changing some of these will bring back the smoothness to your system.

Also, if you remember approximately the time you installed the problematic packages in question, you can open synaptic package manager under: lubuntu options->System Tools->Synaptic... and from there you can go to: File->History 
i) either check by date or
ii) type qt and see which packages will get displayed

By remembering the approximate date and combining it with the information received from s.p.m you might be able to remove the packages that trouble your system.

Some additional ideas,
Regards

---


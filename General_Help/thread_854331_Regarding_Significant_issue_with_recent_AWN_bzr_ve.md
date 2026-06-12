---
title: "Regarding Significant issue with recent AWN bzr versions."
date: 2008-07-09
forum: General Help
---

### Post by moonbeam on 2008-07-09
2nd Update:

The awn-testing ppa has been refreshed.  This update does involve the moving of some installed files.  If all goes well it should be handled more or less transparently by the installation.  Feel free to report issues here but it would be greatly appreciated if any significant issues are reported at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) or [https://bugs.launchpad.net/awn-extras/](https://bugs.launchpad.net/awn-extras/) for applet specific bugs.

thanks,


1st Update:

Currently the PPA was reverted to an earlier state.  New debs are being created/tested to try and make the necessary changes as painless as possible.

I'll post again when those packages become available.

Thanks,



---- Original Post ----

There have been some recent changes in awn that will be affecting those of you who use a PPA package from awn-testing and recocard's PPA.

I'd like to extend the apologies of the awn development team as a recent (needed) change had consequences that should have been noticed and possibly handled in a manner that was less burdensome for our users.

I'll update this post soon with more detailed information but in the short term:

1) If you haven't upgraded from the PPA in the last 24 hours then you're probably unaffected.  Don't upgrade until further info is posted here.

2) If you have upgraded a fix is to remove the applets and add them again.  NOTE you may LOSE configurations for several applets and need to reconfigure.  Also don't be surprised if this needs to be repeated on the next PPA upgrade.  

More info including how to resolve the issue without needing to reconfigure any applets will follow soon.

Once again, apologies from the awn dev team.

---

### Post by 16777216 on 2008-07-09
I noticed this morning, and the first thing I did was to remove/replace everything.
But, as I am using a "testing" PPA this is what I expect.

---

### Post by Sealbhach on 2008-07-09
Thanks for the info.


.

---

### Post by moonbeam on 2008-07-09
Currently the PPA was reverted to an earlier state. New debs are being created/tested to try and make the necessary changes as painless as possible.

I'll post again when those packages become available.

Thanks,

---

### Post by moonbeam on 2008-07-10
The awn forums thread where we post info on  this:

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true)

---

### Post by Chang An on 2008-07-11
I had to re add all my applets after the upgrade and now the Notification area applet does not work.  I'm sure you guys are on top of it though.  :)

---

### Post by pcolamar on 2008-07-12
I have followed the downgrade instaction but I do not see any applet in the configuration panel anylonger.

Synaptics says thay are installed, any suggestion ?

How can I check if they are really installed?

Thanks

Palmer

---

### Post by moonbeam on 2008-07-12
> **pcolamar said:**
> I have followed the downgrade instaction but I do not see any applet in the configuration panel anylonger.

Synaptics says thay are installed, any suggestion ?

How can I check if they are really installed?

Thanks

Palmer

Which downgrade instructions?

Which repo are you using?

---

### Post by pcolamar on 2008-07-13
All solved with today's update.

Cheers

---

### Post by detroit/zero on 2008-07-13
I've noticed that with whatever update came through today, my logoff/quit applet has been using some random icon from some random icon theme (i.e., not the theme I'm currently using).

There doesn't seem to be a setting to change the icon for that applet. I've searched in ~/.config and in /usr/share/avant-window-navigator for a way to change it but I haven't figured it out yet.

Removing and re-adding the applet has no effect. Rebooting also has no effect.

As per the AWN forum post, in config-editor I see that all the application paths have been changed fro lib/awn to /usr/share. Config editor also shows that all the applets are pointed towards the correct icon theme and are set to use the icons I want.

One other oddity - I've noticed my main menu applet and the places applet now have to be clicked on to close them after normal use. For example, after selecting a menu item, say, Internet>Firefox, Firefox opens, but the main-menu window is still on the screen. If I open the Places applet and select my home folder, or any other folder, a nautilus window comes up but the places applet (and the whoke AWN bar) is still visible over top of it until I click to close it.

If I click in the nautilus window (or firefox or whatever) to give my application focus, the bar and the applets disappear, but I need to close and restart AWN for those two applets to work again.

Just thought I'd add my peculiarity to the list..


I'm using reaocards repo, btw..

---

### Post by moonbeam on 2008-07-13
> **detroit/zero said:**
> I've noticed that with whatever update came through today, my logoff/quit applet has been using some random icon from some random icon theme (i.e., not the theme I'm currently using).

There doesn't seem to be a setting to change the icon for that applet. I've searched in ~/.config and in /usr/share/avant-window-navigator for a way to change it but I haven't figured it out yet.

Removing and re-adding the applet has no effect. Rebooting also has no effect.

As per the AWN forum post, in config-editor I see that all the application paths have been changed fro lib/awn to /usr/share. Config editor also shows that all the applets are pointed towards the correct icon theme and are set to use the icons I want.

One other oddity - I've noticed my main menu applet and the places applet now have to be clicked on to close them after normal use. For example, after selecting a menu item, say, Internet>Firefox, Firefox opens, but the main-menu window is still on the screen. If I open the Places applet and select my home folder, or any other folder, a nautilus window comes up but the places applet (and the whoke AWN bar) is still visible over top of it until I click to close it.

If I click in the nautilus window (or firefox or whatever) to give my application focus, the bar and the applets disappear, but I need to close and restart AWN for those two applets to work again.

Just thought I'd add my peculiarity to the list..


I'm using reaocards repo, btw..

1) Regarding Quit applet.  Try dragging and drop the icon you'd like to use not the applet itself.  If it doesn't work try again next update.

2) Regarding the focus loss issue.  In configuration check /apps/avant-window-navigator/applets/shared/dialog_focus_loss_behavior   Make sure it's checked.  I'm thinking that there may be a schema issue where the default value isn't getting properly set.

---

### Post by detroit/zero on 2008-07-13
> **moonbeam said:**
> 1) Regarding Quit applet.  Try dragging and drop the icon you'd like to use not the applet itself.  If it doesn't work try again next update.

2) Regarding the focus loss issue.  In configuration check /apps/avant-window-navigator/applets/shared/dialog_focus_loss_behavior   Make sure it's checked.  I'm thinking that there may be a schema issue where the default value isn't getting properly set.
I tried the drag & drop solution.. no dice this time. I'll try again after the next update like you suggest.

I checked the focus behavior key, and much to my surprise, the dialog_focus_loss_behavior didn't exist. The shared section was empty. I created the key, set the value type to boolean, and checked it off. All seems well on that front.

Thanks for the ideas!

---

### Post by detroit/zero on 2008-07-14
The focus behavior seems to be working properly now, so that's a good fix to know.

No luck changing that icon even after today's update, though. I did find the icon the applet is using, and it is part of my selected icon theme, only it's not the scalable gnome-session-end icon, it's a application-close icon from like the 72x72 folder.

Since, as far as I can tell, the icon is used for absolutely nothing anyways, I'm thinking of deleting it and replacing the gnome-session-end icon and renaming it. Think it'll work?

---

### Post by moonbeam on 2008-07-14
> **detroit/zero said:**
> 

No luck changing that icon even after today's update, though. I did find the icon the applet is using, and it is part of my selected icon theme, only it's not the scalable gnome-session-end icon, it's a application-close icon from like the 72x72 folder.

Since, as far as I can tell, the icon is used for absolutely nothing anyways, I'm thinking of deleting it and replacing the gnome-session-end icon and renaming it. Think it'll work?

Probably not.  Or more accurately it's likely to break other things.  I'd leave it be for now.

---

### Post by detroit/zero on 2008-07-16
It would have broke some things. Or, just made them uglier, anyway. That icon being used was for the close program option in File menus inside app windows like Firefox or Nautilus. Had I renamed it, my session-suspend icon would have gone in its place.

The drag&drop fix worked like a charm after todays update. Thanks!

---

### Post by moonbeam on 2008-07-16
The awn-testing ppa has been refreshed.  This update does involve the moving of some installed files.  If all goes well it should be handled more or less transparently by the installation.  Feel free to report issues here but it would be greatly appreciated if any significant issues are reported at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) or [https://bugs.launchpad.net/awn-extras/](https://bugs.launchpad.net/awn-extras/) for applet specific bugs.

---


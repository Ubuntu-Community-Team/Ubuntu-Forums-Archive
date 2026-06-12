---
title: "Firefox - how to restore previous sessions"
date: 2016-09-22
forum: General Help
---

### Post by satimis on 2016-09-22
Hi all,

Ubuntu 16.04
Gnome desktop

Recently Firefox doesn't work properly at start.  After booting up the PC I have to click its icon "Firefox Web Browser" twice to start it.

The tab "restore previous sessions" is at the bottom.  I have to click it to restore previous session.

I just start the PC.  It also needs clicking the above icon twice to start Firefox.  But it is a new "Firebox Web Browser" session without the tab "restore previous sessions" at bottom

I found;
firefox does not restore previous sessions anymore
[https://support.mozilla.org/en-US/questions/1084632](https://support.mozilla.org/en-US/questions/1084632)

But it doesn't help me out.  Please help "How to restore previous sessions".  Thanks

Regards
satimis

---

### Post by Bucky Ball on 2016-09-22
I use the Session Manager add-on for Firefox. Check Tools> Add-ons ... and do a search, install.

---

### Post by ajgreeny on 2016-09-22
And I use **Tab-Mix-Plus** add-on which offers many tab management options including its own session restore.

Worth a try I think.

---

### Post by satimis on 2016-09-22
> **Bucky Ball said:**
> I use the Session Manager add-on for Firefox. Check Tools> Add-ons ... and do a search, install.
Hi,

Thanks for your advice.

I have session-manager installed on Firebox.  Reboot PC and start Firefox Web Browser.  But I couldn't find the Restore Session tab on the bottom of the browser.

Previously I have 3 Firefox web browser windows running with several tabs running on each window without saving.

Then
Tools -> Session Manager -> Restore Session

The tab [Restore] on the browser doesn't respond on clicking it

Regards
satimis

---

### Post by satimis on 2016-09-22
> **ajgreeny said:**
> And I use **Tab-Mix-Plus** add-on which offers many tab management options including its own session restore.

Worth a try I think.
Hi,

Thanks for your advice.

Could I install Tab-Mix-Plus if Session-Manager is installed and running.

What I expect to restore is the 3 Firefox web browser windows, each with several tabs running.  For unknown reasons on starting the PC and starting Firefox I have to click twice the icon.  The tab "Restore Previous Session" is not found at the bottom of browser.

Regards
satimis

---

### Post by dragonfly41 on 2016-09-22
Try setting the properties of your Firefox launcher to .. [COLOR=#0000ff]firefox -p %u[/COLOR]

or run that command in terminal.

This launches session manager every time so you can choose your profile/session.

---

### Post by Bucky Ball on 2016-09-22
Session Manager should run by default with Firefox anyway. The icon will be in the toolbar next to the address box and the search box to the right. Alternatively, Tools> Session Manager. No need to do any other steps, or shouldn't be. Just launch Firefox. If you can't access it, there's a problem elsewhere, probably with Firefox or your profile.

---

### Post by ajgreeny on 2016-09-22
> **satimis said:**
> Hi,

Thanks for your advice.

Could I install Tab-Mix-Plus if Session-Manager is installed and running.

What I expect to restore is the 3 Firefox web browser windows, each with several tabs running.  For unknown reasons on starting the PC and starting Firefox I have to click twice the icon.  The tab "Restore Previous Session" is not found at the bottom of browser.

Regards
satimis
You will get the option in TMP preferences to use either its own Session-Restore or to still use the FF Session-manager to restore things.
Personally I don't use either as I prefer a clean start each time, so I can't comment on any differences between the two.

---

### Post by dragonfly41 on 2016-09-22
> [COLOR=#000000]If you can't access it, there's a problem elsewhere, probably with Firefox or your profile.

That is why I suggested the -p argument since a new profile can be created *before* firefox is launched.[/COLOR]

---

### Post by satimis on 2016-09-22
> **Bucky Ball said:**
> Session Manager should run by default with Firefox anyway. The icon will be in the toolbar next to the address box and the search box to the right. Alternatively, Tools> Session Manager. No need to do any other steps, or shouldn't be. Just launch Firefox. If you can't access it, there's a problem elsewhere, probably with Firefox or your profile.
Hi,

Tools -> Session Manager

Closes-tabs: is grey out

there are;
2  Add-ons manager
3  Preference

I only need one of them.  How to remove the rest?

Thanks

satimis

---

### Post by Bucky Ball on 2016-09-22
Menu button in far right of same bar (three horizontal lines)> Customise or just right click and remove the ones you don't want.

---

### Post by satimis on 2016-09-23
> **Bucky Ball said:**
> Menu button in far right of same bar (three horizontal lines)> Customise or just right click and remove the ones you don't want.
The customize window is attached.  I couldn't find those unneeded items.  Which tab I have to drill down?  Thanks

satimis

---

### Post by Bucky Ball on 2016-09-23
Grab the icons from your toolbar and drop them in the window with the other icons to remove them from the taskbar.

---

### Post by satimis on 2016-09-23
> **Bucky Ball said:**
> Grab the icons from your toolbar and drop them in the window with the other icons to remove them from the taskbar.
Please advise which icons and toolbar?  In the customize window?  Thanks

satimis

---

### Post by ajgreeny on 2016-09-23
All the icons in your toolbar, both wanted and unwanted, will still be showing in the FF toolbar at the top of the FF window.

Choose those that you do not want to keep in your toolbar and simply drag them out of the toolbar into the customise window.  We don't know what you wish to keep so that decision will have to be yours, and yours alone.

---


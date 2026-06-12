---
title: "Thunderbird + Lightning + Calendar"
date: 2014-04-18
forum: General Help
---

### Post by Pollik on 2014-04-18
I am still very much a novice with Linux 12.04 LTS, but I am familiar with Thunderbird in WIndows

I added the extensions for Lightning and Calendars, with the intention of linking to shared Google calendars.

It all worked fine until I got to one particular calendar (belonging to someone other than me) which is set to issue visible reminders.  What happens is that on launching TB, the reminders appear immediately (as they should), but then gray out the TB screen behind the reminders (as they shouldn't), making TB completely inaccessible.  I have tried to dismiss or snooze the reminders, but nothing happens.

In this state, I cannot access TB's menus to remove the extensions.

I have tried uninstalling TB twice, but on each reinstall, the extensions are still installed, and I still cannot access TB's menus.

Using Nautilus, I can see that there are a number of TB related files remaining after uninstallation...mostly they seem to be locked.  Leastways, they display a padlock icon and I can't simply delete them.

Other information:  that same calendar is also a minor problem in TB in Windows (haven't figured out why), but there I am able to close the notification window and regain control of TB, something which I cannot do in Ubuntu.

I'd be grateful for any ideas, please.  I am really not good on using Terminal, but I can follow instructions if you treat me as a complete newb.

Many thanks in advance


Polly

---

### Post by TheFu on 2014-04-18
Shutdown thunderbird
```
mv ~/.thunderbird ~/.thunderbird.old
```
Start thunderbird

This will move the settings out of the way.

---

### Post by Pollik on 2014-04-18
Brilliant...thank you :)

---


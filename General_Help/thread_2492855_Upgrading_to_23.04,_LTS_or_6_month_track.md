---
title: "Upgrading to 23.04, LTS or 6 month track?"
date: 2023-11-25
forum: General Help
---

### Post by Advait on 2023-11-25
I'm currently on 22.04.3 LTS.

```
advait@advait-Bravo-15-A4DDR:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy
advait@advait-Bravo-15-A4DDR:~$ 

```
 
After using Software Updater, it asks me if I want to upgrade to 23.04. If I upgrade to 23.04, will that keep me on the LTS track? Or will the upgrade to 23.04 move me to the 6 month release track?

Also, what is the official name for the 6 month release track?

---

### Post by Dennis N on 2023-11-25
Being on the LTS track just means you use an LTS version and want to be notified to upgrade to the next LTS release only. Since you are being notified of 23.04, you are not set on the LTS track.

If you want to be on that track and only use LTS releases, then set:
Software & Updates > Updates Tab > "Notify me of a new Ubuntu version:"
to:
"for long-term support versions"
Then you can say you are on the LTS "track".

You are being offered 23.04 because yours is set to "for any new version". When set that way, you get an availability notice for the next available supported release, not always the latest.

---

### Post by ian-weisser on 2023-11-25
> **Advait said:**
> Also, what is the official name for the 6 month release track?

It has had several informal names, none official.

Classically, the 6-month track was known as "Standard." In earlier days, LTS was much less popular. LTS was originally developed as a somewhat special case for enterprise use. Enterprises complained that every 6 months kept breaking their workflow.

More recently, LTS has become much more popular than 6-month so "standard" is no longer the standard for most. The current name en vogue is "Interim." However, in English that term also suggests 'incomplete', so some folks confuse it to mean 'beta.' It's complete and tested. It's not beta. It's stable. It merely has a short life.

Many folks around here simply refer to the track as the "6-month" releases. Clear and understandable.

---

### Post by Advait on 2023-11-25
> **Dennis N said:**
> Being on the LTS track just means you use an LTS version and want to be notified to upgrade to the next LTS release only. Since you are being notified of 23.04, you are not set on the LTS track.

If you want to be on that track and only use LTS releases, then set:
Software & Updates > Updates Tab > "Notify me of a new Ubuntu version:"
to:
"for long-term support versions"
Then you can say you are on the LTS "track".

You are being offered 23.04 because yours is set to "for any new version". When set that way, you get an availability notice for the next available supported release, not always the latest.

Cool. I made the change. Thanks.

---


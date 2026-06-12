---
title: "Evolution filters aren't filtering"
date: 2006-10-10
forum: General Help
---

### Post by jrjazzman on 2006-10-10
I'm running Evolution 2.6.1 on Ubuntu 6.0.6.  I added a couple of inbound message filters in Evolution, however they aren't firing.  Both of the filters are simple and the action is to delete.  Is there something that has to be done to turn filters on, other than creating the filters?

thanks

---

### Post by dcstar on 2006-10-11
> **jrjazzman said:**
> I'm running Evolution 2.6.1 on Ubuntu 6.0.6.  I added a couple of inbound message filters in Evolution, however they aren't firing.  Both of the filters are simple and the action is to delete.  Is there something that has to be done to turn filters on, other than creating the filters?

thanks

No, post some screen shots of the filters.

---

### Post by jrjazzman on 2006-10-12
Attached.

> **dcstar said:**
> No, post some screen shots of the filters.

---

### Post by saracen on 2006-10-12
Yeah, i'm having this as well.  My filters aren't filtering automatically.  But if I select all my messages and choose Message -> Apply Filters, then they get filtered.  So I have to do it manually each time :(

---

### Post by saracen on 2006-10-12
OK, I figured this one out.  You have to go into Edit -> Preferences.  Then select the mail account you want the filters to work on and click 'Edit'.  Then navigate to the "Receiving Options" tab and make sure that the "Apply filters to new messages in Inbox on this server" button is checked.

What a hassle.  All these config options are way too hidden and they're all over the place.  :-?

---

### Post by jrjazzman on 2006-10-12
Pretty unintuitive.  Unfortunately, I don't have the "Apply filters to new messages in Inbox on this server" option.  I'm running Evolution 2.6.1.  What is your version?

> **saracen said:**
> OK, I figured this one out.  You have to go into Edit -> Preferences.  Then select the mail account you want the filters to work on and click 'Edit'.  Then navigate to the "Receiving Options" tab and make sure that the "Apply filters to new messages in Inbox on this server" button is checked.

What a hassle.  All these config options are way too hidden and they're all over the place.  :-?

---

### Post by saracen on 2006-10-13
I'm running Edgy - so version 2.8.1  I guess try and look for something similar... I think I read about this in a post that was pretty old, so there's probably something in older versions as well.

---

### Post by zneastman on 2006-11-08
I'm having the same problem, at least on my main (IMAP) mailbox.  That is, if I manually select any number of emails and hit Ctrl+Y to apply the filters, the mail gets filtered no problem.  But it doesn't get filtered automatically, even though I've checked the "apply filters to the INBOX" box in the account's preferences.

This may be related to another bug, where Evolution hangs for a long, long, long, long time (sometimes an hour, but for the hell of it I let it once go overnight) while trying to open the first message in my IMAP mailbox.  Of course this combination of bugs makes Evolution totally unusable, which really is a shame; I'd much rather be using Epiphany/Evolution than Firefox/Thunderbird, since F/T needs better desktop integration (e.g. with calendering, gnome-pilot, HIG, and so on) before I'ma call them sexy.

---


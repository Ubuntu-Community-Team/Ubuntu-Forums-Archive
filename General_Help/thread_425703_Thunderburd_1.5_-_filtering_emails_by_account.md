---
title: "Thunderburd 1.5 - filtering emails by account"
date: 2007-04-27
forum: General Help
---

### Post by geekphreak on 2007-04-27
I use TB 2.0 on Windows and I can filter all messages and put them in separate subfolders of global Inbox by account. So, I have Gmail 1, Gmail 2, etc. inside my Inbox folder and when a message arrives it is routed to the corresponding folder. 
How do I do this in TB 1.5? Filter rules are different, and whatever I try does not seem to work. TB knowledge base says it can be done, but not how to do it.

Any help is appreciated.

---

### Post by mac.ryan on 2007-04-27
I would simply make a set of filtering rules triggering on the "to" field: if a mail has been sent to "jo.doe@gmail.com" move it to "folder 1", if to "jo.doe@hotmail.com" move it to "folder 2", etc...

---

### Post by Erlander on 2007-04-28
I have just changed from windows to Ubuntu for Thunderbird.

I copied my profile from Windows into Ubuntu and all the filters work.

I filter mail from 3 email accounts into 9 different mail folders.  Criteria vary from who addressed to to subjects lines (used for mail from Yahoo Groups and other email lists).

In windows your profile is in Documents & settings/Your-User-Name/Application data/Thunderbird/Profiles/randomstring.default

In Ubuntu the profile is in /home/your-user-name/.mozilla-thunderbird/randomstring.default

To copy the profile across copy the contents of the folder with the random string as its name and paste into the Ubuntu folder with the random string as its name.

This copies over all your mail, filters and settings.

I hope this helps.

Rob

---


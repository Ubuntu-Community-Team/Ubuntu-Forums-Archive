---
title: "evolution encoding problem"
date: 2005-08-09
forum: General Help
---

### Post by 23meg on 2005-08-09
I'm having trouble with some Turkish (ISO-8859-9) encoded characters in Evolution's upper pane where mail headers are displayed. I can't exactly narrow down the problem to specific mailers; most corrupt headers are in multipart messages sent with Microsoft Outlook Express, but not all, and everything is fine in the message body, only "From" and "Subject" headers often have corrupt characters. 

Is there a preference file somewhere that i have to tweak in order to set a different encoding for the upper pane? Or some other tweak I need to perform in order to get things right? Any ideas?

---

### Post by charlieg on 2005-08-09
It sounds more like a bug either in the way Evolution was built for Ubuntu or Evolution itself.

---

### Post by 23meg on 2005-08-11
May this have something to do with GNOME locales? I'm using the English locale, not Turkish.

---

### Post by Fred_and_ro on 2007-11-23
any updates to this? I've just started searching the forums, having the same trouble myself with Evolution.
I'm using Ubuntu 7.10 with Evolution 2.12.1 and Gmail IMAP.

For testing, I have switched to pop in Gmail and Evolution, and this works just fine, so I'm thinking it has to do with IMAP support, but not sure if I should look to Gmail or Evolution (or both) to fix things for myself.

Oh - and in Evolution I have the Preferences > Encoding set to UTF-8 for both the reader and composer, and in Gmail I have also set UTF-8 as encoding.

---

### Post by 23meg on 2007-11-27
I remember locating what I think is the corresponding bug report for this issue in the [GNOME bug tracker]("http://bugzilla.gnome.org/"), but I can't at the moment. Have you found or filed one? 

If I recall correctly, it was a WONTFIX; it was determined that the source of the problem wasn't in Evolution but some other clients, and "fixing" it in Evolution would actually mean breaking what should be correct behaviour. But again, this may not be correct bug report.

---

### Post by Fred_and_ro on 2007-11-28
@23meg: hey, thanks for replying.
No, I haven't found or filed a bug report for this..my bad.

> If I recall correctly, it was a WONTFIX; it was determined that the source of the problem wasn't in Evolution but some other clients, and "fixing" it in Evolution would actually mean breaking what should be correct behaviour. But again, this may not be correct bug report.

You're probably right - my prime suspect is my installation of Ubuntu, I think there is a conflict with the locales settings. Tried to mess around with it, but to no luck.

Anyway - I've moved on to Thunderbird now - for a separate issue with searching Contacts inside Evolution (however, I understand that a fix is coming for that). I'm using it with Gmail, and with the Lightning calendar extension is does what I need it to do. I will look into Evolution again when it has full read-write capabilities with the Google Calendar.

---


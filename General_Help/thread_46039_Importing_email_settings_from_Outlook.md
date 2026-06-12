---
title: "Importing email settings from Outlook"
date: 2005-07-02
forum: General Help
---

### Post by zoqaeski on 2005-07-02
G'day peoples
Before I installed Linux, I backed up all of my emails and settings and everything from Outlook (not Express) into one big *.pst file. Now I cannot load it into the Evolution mail client programme; it just returns an error saying "No importer available for XXXX_XX.pst".

Does anyone know how to fix up this problem, or how to get the importing tool? If I can't get all of these settings back, then I've lost all of my mail and contacts and everything from before my Linux Upgrade ](*,) 


Robbie

---

### Post by arnieboy on 2005-07-03
There are many ways to do this.  However, if you want to preserve timestamps, attachments etc, there is only one correct way to do this:

If you have access to an IMAP server, you could open your .pst in Outlook and move all the messages back up to an IMAP server. Once everything was moved off of the PST and up to IMAP, you should very easily set up Thunderbird to access all your messages from the IMAP server.

Hope this helps.

---

### Post by jeremy on 2005-07-03
You could download and install Outport and use that to export your Outlook data to a format that can be imported by evolution (I have used this and it worked fine).
[http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/Outport.shtml](http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/Outport.shtml)

---

### Post by jeremy on 2005-07-03
I just re-read your post, and saw that you had said 'settings', outport won't export your e-mail accounts, but it will export your mail folders, contact list, calendar appointments etc.

---

### Post by arnieboy on 2005-07-03
[QUOTE=jeremy]You could download and install Outport and use that to export your Outlook data to a format that can be imported by evolution (I have used this and it worked fine).
[http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/Outport.shtml](http://www.softpedia.com/get/Internet/E-mail/Mail-Utilities/Outport.shtml)[/QUOTE]
 
What is the format that Outport saves it as?
This certainly looks like an easier procedure but I personally prefer Thunderbird over Evolution. Can Thunderbird import these files (or import them from evolution)?

---

### Post by jeremy on 2005-07-04
I can't remember which format, but am pretty sure that you could then import to thunderbird too.
Alternatively you could install thunderbird in windows, and import directly from outlook, then copy over to linux.
There is more info about outpost at [http://outport.sourceforge.net/](http://outport.sourceforge.net/) (I really should have posted this link in the first place, rather than the other), including details of formats. I have used it to migrate both outlook XP and outlook 2003 .pst files without any problems.

---


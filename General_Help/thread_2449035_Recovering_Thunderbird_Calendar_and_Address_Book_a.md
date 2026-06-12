---
title: "Recovering Thunderbird Calendar and Address Book after crash"
date: 2020-08-18
forum: General Help
---

### Post by cscj01 on 2020-08-18
I am on Ubuntu 18.04 x64 and Thunderbird 68.10.  I had a system crash and had to restore from a backup.  That was successful.  Everything was okay as of the date of the backup.  After upgrading all my software, Thunderbird would no longer download from my gmail account.  After trying everything I could find through Internet searches, I deleted the original gmail IMAP account from Thunderbird and tried to create it again.  I kept getting a message saying the server existed, so I couldn't create the account.  Finally, I deleted all profile folders except the original.  That worked, and I was able to create the account and get all my emails.  It had been so long, I had forgotten that the calendar was an Add-On, so I had none of my appointments and tasks.  Additionally, my Address book was gone.  I did install the Lightning Calendar Add-On, but of course, there were no entries.

Since all of this information existed on my backup, I assumed that I could mount that drive (an external desktop USB) and retrieve the requisite information.  However, Ubuntu refuses to let me mount the drive.

Any suggestions on how to proceed will be appreciated.

---

### Post by TheFu on 2020-08-18
The current release of thunderbird doesn't need/use Lightning. 
I won't use google stuff, so can't help with that. Sorry.

I do use remote calendars, ldap address books and multiple imaps accounts.  The remote calendars lose credentials too often. Don't know why and thunderbird forum answers haven't offered and solution that worked.
Current;y have; 68.10.0 (64-bit)

---

### Post by ajgreeny on 2020-08-18
How did you add lightning?

For some time now I have always used the repository package **xul-ext-lightning** and not added it from the T'bird extensions site.
The repo version always works fine but the extensions site version was a bit of a problem last time I tried it, though that was a long time ago.
I am also using T'bird 68.10.0

---

### Post by TheFu on 2020-08-18
Lightning is built-into the current Thunderbird release. Not needed.
[https://support.mozilla.org/en-US/questions/1296158](https://support.mozilla.org/en-US/questions/1296158) explains how to get google-calendar. I don't know if this works or not. Don't need that stuff to work with Zimbra or for local calendars.

---

### Post by rbmorse on 2020-08-18
The address book should be in your backup in the file ~/.thunderbird/*your user profile/*abook.mab   

I don't know if it still works, but you used to be able to copy an old address book over the new .mab file, restart Thunderbird and your
old addresses would appear as if by magic.  Worth a try. Backup the current abook.mab before, of course.

---

### Post by cscj01 on 2020-08-18
Thanks for the replies.  I was able to get my addresses from abook.mab.  I added the calendar with the Lightning extension.  I think TB V 78 is when you get the built in calendar.  According to what I have read, my calendar is in a SQLite database called storage.sdb.  I'm not sure there is anything there.  When I left click on the storage.db, I get a prompt saying "Open with DB Browser for SQLite".  When I click on that, I see certain statements such as Create Table.  If I click on the Browse Data tab, I don't see any data.

---

### Post by TheFu on 2020-08-18
SQLite is a lite version of a file based SQL DB.  It is the most popular DB in the world for a few reasons - mainly because it is F/LOSS and small.  It is not a place to store important data for a business. It is NOT ACID compliant, which matters for real DBMS solutions.  But often, with a tiny number of concurrent users, it is perfectly fine.  My blog used SQLite until it couldn't handle the performance of thousands of hits an hour.

Anyways, if you don't know SQL, best not to touch or open, those files.

Lightning isn't just for local calendars. It deal with ical and caldav calendars on the network too.  We aren't limited to a single calendar. I have 7 different calendars each for different needs. 3 are from external sources, 4 are under my control for different stuff.  Personal, Holidays, Work, and Home Maintenance Tasks (mostly when to inspect things, trim hedges, clean gutters, fertilize, and replace filters... ).  The Personal one had all sorts of things - reminders for changing contact lenses, birthdays of family and friends with a 7 day lead, when property taxes are due, when to renew my website HTTPS certs or renew my domains - for example, my main domain registration ends in a few weeks, so I'm watching for coupon codes to get it for as cheap as possible the next 10 yrs. It is too much hassle to get for shorter periods. Once every ten years means I need a reminder.  Anyways, there's all sorts of things in my calendar as future reminders, not just meetings.

---

### Post by ajgreeny on 2020-08-19
> **TheFu said:**
> Lightning is built-into the current Thunderbird release. Not needed.
[https://support.mozilla.org/en-US/questions/1296158](https://support.mozilla.org/en-US/questions/1296158) explains how to get google-calendar. I don't know if this works or not. Don't need that stuff to work with Zimbra or for local calendars.
But that is for T'bird 78.
The OP and most of us are using the repository version of T'bird which is still 68, so lightning as a separate package or add-on is still necessary for that.

---

### Post by TheFu on 2020-08-19
> **ajgreeny said:**
> But that is for T'bird 78.
The OP and most of us are using the repository version of T'bird which is still 68, so lightning as a separate package or add-on is still necessary for that.

Wow! You are very correct.  I saw the "8" and my eyes filled in the "78" from the "68".  Sorry folks. I remember the announcement from about a month ago and being a little afraid about the change. Then got an update and assumed it was the scary one. Plus somethings that had been broken for me in Thunderbird started working again - mostly calendar stuff.  

Once again, I ignored reality and inserted my own world view. ;)

---

### Post by ajgreeny on 2020-08-19
Don't worry about it. We've all done that!

I know I have on occasion, reading what I expect or want to read, rather than what is actually written.

---

### Post by cscj01 on 2020-08-24
I have recovered the calendar with SQLite and storage.sdb.  So I will close this thread.

---

### Post by ajgreeny on 2020-08-24
You can not personally close a thread; only forum staff can do that.

However ,please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. 
It is a great help to other users searching the forum.

---


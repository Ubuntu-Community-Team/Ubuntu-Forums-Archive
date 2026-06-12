---
title: "How does Evolution IMAP work?"
date: 2005-10-20
forum: General Help
---

### Post by dave9191 on 2005-10-20
Hey guys,

I seem to be having a bit of a problem with evolution and IMAP. It access the server and new mail. But when I delete mail it doesnt get moved into my trash folder. It just gets crossed out and hidden and I can expunge it to remove it permentatly. And it doesnt update the IMAP server so all my deleted mail is still in the folders when i use other mail clients on other machines. 

Same applies to moving mails to other folders. They get moved in evolution, but not on the server. 

I would love to use evolution for mail, tasks and calendar. I just love the idea of it intergrating with the drop down cal on the clock. But if I can't get it to work properly then I'll need to use something like thunderbird. 

Dave

---

### Post by castrojo on 2005-10-20
This is the way evolution works. It does an IMAP delete, which means it marks the mail for deletion in your inbox until you expunge. Delete as in "move it to the trash" is pop-like behavior, which tbird emulates even when using imap. 

If you search the gnome bugzilla you'll find plenty of people who want evo to just move the mail to a trash folder. Unfortunately no one is listening. I wish Evo had this as an option, but it doesn't, so I'm using thunderbird also.

---

### Post by dave9191 on 2005-10-21
Hey, thanks for the reply. 

What about moving messages from folder to folder? Surley it should make those changes on the server. 

I'm a bit dissapointed about this, I haven't used a IMAP client that didnt have the option to choose the trash folder on your server yet :(

What about intergrating other programs with the gnome drop-down-calendar to list tasks and today appointments ? 

Dave

---

### Post by doclivingston on 2005-10-21
[QUOTE=dave9191]What about moving messages from folder to folder? Surley it should make those changes on the server.[/quote]

Yes. Moving to anywhere but the trash and junk acts as expected - both of those are done using virtual folders, not real ones.

> What about intergrating other programs with the gnome drop-down-calendar to list tasks and today appointments ?

Those are done using evolution-data-server, so you don't actually need the Evolution application to use them. However I'm not aware of anything yet that talks to E-D-S, besides the gaim plugin to synchronise your buddies.

---

### Post by piedamaro on 2005-10-21
"What about moving messages from folder to folder? Surley it should make those changes on the server.

Yes. Moving to anywhere but the trash and junk acts as expected - both of those are done using virtual folders, not real ones."

...ehr, wrong ;) IMAP server works with spool dirs (/var/spool/mail/<user name>) and when you create a folder it creats a real folder under the user's home directory (on hthe server). In the end everything is stored on the server.

---

### Post by doclivingston on 2005-10-21
[QUOTE=piedamaro]...ehr, wrong ;) IMAP server works with spool dirs (/var/spool/mail/<user name>) and when you create a folder it creats a real folder under the user's home directory (on hthe server). In the end everything is stored on the server.[/QUOTE]

For me, Evolution just uses virtual folders to Trash and Junk. So if I mark a message from my Inbox as junk, and then check my mail via some other method, it will still be in my Inbox.

---

### Post by piedamaro on 2005-10-21
Yes, you are right. I had misunderstood. I was refferring to the creation of normal imap folders :) That's beacuse with IMAP (in online mode) mail messages are *tagged* as "answered" "deleted", etc.

---

### Post by jonesy on 2005-10-21
You can set evolution to expunge folders on exit so that when you go home, etc and login with another client everything should be up-to-date.

---

### Post by dave9191 on 2005-10-21
[QUOTE=jonesy]You can set evolution to expunge folders on exit so that when you go home, etc and login with another client everything should be up-to-date.[/QUOTE]

Yeh, but that still has a few problems. I want it to move mails to the trash folder I have on the imap server rather then delete them. And I don't turn evolution off. I just suspend my laptop. But on occasion I log in from uni computers or another home machine using another imap client. 

Dave

---


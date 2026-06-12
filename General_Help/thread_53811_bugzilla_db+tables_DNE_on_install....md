---
title: "bugzilla db+tables DNE on install..."
date: 2005-08-02
forum: General Help
---

### Post by taryneast on 2005-08-02
I recently decided to install bugzilla (latest version through apt - I'm using latest dist-upgrade of Hoary) and went through the whole thing of installing mysql and apache and getting them up and running etc - seemed to be just fine. 

I installed bugzilla and it gave me all sorts of errors - I went through a process of giving the correct permissions to the bugzilla directories when I started getting errors.

Starting with (and I paraphrase) "database 'bugs' doesn't exist"... so I created one... 
Then it told me that the 'bugs' username did not have permission to access the database. 
Firstly I had to create the user...
then I went wandering through the config files and tried to add the password to the appropriate place (right where it says "password" right next to where it has "username = 'bugs'" or similar in globals.pl). That didn't work so I temporarily just removed the password for the 'bugs' user from the db (I don't like that - as an aside, how do I set it up to use the password?).

That let me at least see index.cgi - at which point I thought I was going just fine as I could see all the usual startup pages... until I tried to do something useful (like, say add a bug), at which point it berked out and gave me:
**LOCK TABLES shadowlog WRITE,  tokens WRITE: Table 'bugs.shadowlog' doesn't exist**

so I went delving into the tables in mysql... to realise, of course, that there are none. After all I even had to create the bugs database in the frist place <sigh>

So the question is: how do I get the proper database+tables - as it didn't happen automatically when I installed... I also tried doing a reinstall from synaptic - no joy. I am loathe to have to go through the bugzilla doco and build the tables from scratch... :P

Can anyone help?

Thanks heaps,
Taryn

---

### Post by taryneast on 2005-08-03
Well it seems that something in mantis may have been killing it. I unsuccessfully tried to install mantis earlier (before I began with bugzilla) and it had some error that was causing it to "exit with code 1" - so I tried with bugzilla - which seemed to install everything... but also was berking out. I uninstalled mantis, reinstalled bugzilla and all was good with the world.

Taryn

---


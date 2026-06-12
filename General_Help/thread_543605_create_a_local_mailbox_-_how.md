---
title: "create a local mailbox - how?"
date: 2007-09-05
forum: General Help
---

### Post by steve909 on 2007-09-05
Hello all,
I'm trying to create a localhost mail account (user@localhost) to read emails from mdadm using evolution.
When I try to set up an account using 'local delivery' or similar in evolution, it asks for the location of a config file for the mailbox.
There is no config file, where can I find it?

I have no user@localhost file under /var/mail or /var/spool/mail and have followed various posts on here, logging into the console, loading and using mutt, postfix etc but nothing creates a local mailbox. The posts all seem to refer to older versions of ubuntu.

How can I create a local mailbox, and create this config file that evolution needs?

Any help or pointers would be gratefully received! Thanks

using Fiesty 7.04

---

### Post by mocoloco on 2007-09-06
It was a pain for me to find anything that explained it, and I can't find anything again now, so I will go from memory. I tested this on a virtual machine, so I know it works.

If you look in /var/spool/mail you'll see there's nothing there now.
You have to set up your local mailbox, and apparently the easiest way is to send something to it and it will be created.  We also can't send a message with Evolution to localhost until we can setup the account (nice paradox).  So we'll send it from a command line tool.

1) Install "mailx"
```
sudo apt-get install mailx
```
It will walk you through a setup for postfix, the only change will be selecting local only, leave the rest as default.

2) Send yourself a message:
```
mail -s "Nice subject goes here" <yourusername>@localhost
```
It will then let you type in a message body. When done hit Ctrl+D, then just enter when it asks for cc.  Now if you look in /var/spool/mail you'll see a file named after your user. 
You can also see your mailbox from the command line by just typing "mail".  I don't know all the commands, other than q to quit :).

3) Setup Evolution.  Edit -> Preferences.  
Under "Mail Accounts" do "Add".  
For e-mail address type in <username>@<yourhostname>.  
Server type: I couldn't get "local delivery" to work, so pick "Standard Unix mbox spool or directory".  For the path go to /var/spool/mail and pick your user's file.
For sending, change the drop down to use sendmail.
I named my account "Local".  Use whatever you want.

That should be it.

---

### Post by steve909 on 2007-09-06
THANK YOU!

I was going mental searching and trying things suggested in different threads. As simple as that. Unbelievable.
I will now be told if my raid array degenerates.

One thing, sorry to pick, but there was no walk through for postfix as you said. It works, nonetheless.

Mocoloco, King of the forum.

Thanks again

---


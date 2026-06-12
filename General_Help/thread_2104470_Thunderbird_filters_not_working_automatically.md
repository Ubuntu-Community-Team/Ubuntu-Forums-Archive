---
title: "Thunderbird filters not working automatically?"
date: 2013-01-13
forum: General Help
---

### Post by springs1 on 2013-01-13
Hi all,

I've got an installation with Thunderbird Version 17 installed and I'm trying to setup filters for incoming mail. How ever which ever filter I have setup it doesn't seem to work. If i run them manually they do seem to work.

I've tested the same filters on my windows machine with version 17.0.2 and it works for the most part.

Is there a Bug on the linux version that stops this from working?

or does anyone have another way / client i can filter incoming email? All i need to be able to do is run a script when a filter matches certain parameters.

Mail box is a gmail account setup via Imap if it helps.

---

### Post by haqking on 2013-01-13
> **springs1 said:**
> Hi all,

I've got an installation with Thunderbird Version 17 installed and I'm trying to setup filters for incoming mail. How ever which ever filter I have setup it doesn't seem to work. If i run them manually they do seem to work.

I've tested the same filters on my windows machine with version 17.0.2 and it works for the most part.

Is there a Bug on the linux version that stops this from working?

or does anyone have another way / client i can filter incoming email? All i need to be able to do is run a script when a filter matches certain parameters.

Mail box is a gmail account setup via Imap if it helps.

Well works fine for me though I am in slackware.

You can also set your filters on the gmail end which is the best way, as you have IMAP at the moment things are coming in syncing to your client getting filtered/rearranged then syncing back, if you filter server side there is less to do ;-)

---

### Post by apochry on 2013-01-13
## wrong post, deleted ##

Sorry for the inconvenience!

---

### Post by timgood on 2013-01-13
Er, I believe the OP is talking about Thunderbird, not Evolution...?

---

### Post by springs1 on 2013-01-18
the problem with filtering it server side is that i won't be able to run scripts.

What I'm trying to do is email the machine and it runs a predefined script which can't be done by filtering it server side.

---

### Post by SeijiSensei on 2013-01-18
Rather than using Thunderbird for this task, if the machine you are sending the mail to has an MTA installed like sendmail or Postfix, then install the **procmail** package from the repositories.

Procmail enables you to write "recipes" which process messages depending on text it finds in the headers or body.  One thing it can do is pipe the message to a script.

See "[man procmailrc]("http://linux.die.net/man/5/procmailrc")" and for a quick introduction to writing recipes, "[man procmailex]("http://linux.die.net/man/5/procmailex")", for details.

If you need to run the script with root privileges, you can put the recipe in /etc/procmailrc.  That file is used on every message.  User-level recipes are placed in /home/user/.procmailrc and are processed after /etc/procmailrc.

---


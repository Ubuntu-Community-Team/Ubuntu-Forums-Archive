---
title: "Collect and sort mail from a catch-all mailbox"
date: 2008-05-22
forum: General Help
---

### Post by lofgren on 2008-05-22
Hi all,

I have posted in flurdy's howto post for setting up a mail server, but aren't sure how much traffic the howto area sees.
(An excellent mail server HOWTO by the way: [http://ubuntuforums.org/showthread.php?t=185913](http://ubuntuforums.org/showthread.php?t=185913))

**My questions:**
Does anyone have experience in collecting mail from a catch-all mailbox and filtering/forwarding it into postfix virtual mailboxes?
Can you provide any tips or pointers?

I have a godaddy account and have configured a catch-all mailbox. My wife and I send out as various addresses and would obviously like to get our own replies back ;)   Previously I had setup one mail client and just used rules to sort the mail into folders...

A rule/recipe/filter should only need to be simple - sift out my wife's mail and send the rest to me.

The system status at the moment is that I can send mail internally and relay mail back out via godaddy, but I need to work out a way to collect incoming mail. I have amavis/clamav doing content filtering on mail received via port 25, so I would prefer to deliver to postfix to keep that in the loop - rather than deliver to the virtual mail directories.

I have read about and tested fetchmail/getmail/procmail/maildrop. If I understand the concepts correctly, it would seem the common configs for those apps is to forward to maildir/mailbox folders directly. Either that, or the configs people have listed are just simple and use that method.

thanks in advance!
Lofgren

---

### Post by lofgren on 2008-07-02
Workaround:

Okay, I've temporarily given up on collecting my mail and sending it to my internal postfix server (which, as per flurdy's howto, includes amavis/clamav etc).

In the mean time, I am using getmail to collect my mail, with type=multiguesser and a couple of local entries to file my wife's mail into the mail into local maildir's.
The rest of the mail goes to me.

To make use of the already installed clamav, I am using a filter that uses clamav for virus checking.

The filter entry in getmailrc looks like:

Code:
[B][filter-1]
type = Filter_classifier
path = /usr/bin/clamdscan
arguments = ("--stdout", "--log=/home/virtual/.getmail/clamav.log", "-")
exitcodes_drop = (1, )
[/B]


I'm still interested in filing mail via postfix (instead of the direct maildir folders) if anyone has any suggestions.

regards,
Lofgren

---


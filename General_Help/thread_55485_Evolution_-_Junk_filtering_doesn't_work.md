---
title: "Evolution - Junk filtering doesn't work"
date: 2005-08-09
forum: General Help
---

### Post by maxcz on 2005-08-09
Hello,

I've been trying to get the Junk filtering in Evolution work "the right way" but with no success. I'm using Evolution 2.2.2.1, I have set up an IMAP account (the server is Lotus Notes), checked "Check new messages for Junk contents" in account options, checked "Check incoming mail for junk" in mail preferences but the spam filter is not applied on incoming mail, until I use Actions -> Filter junk on selected mail.
I can see this behaviour also with previous (1.x) versions of Evolution. The only solution (more of a workaround) I managed to get working was to set up a separate background script, which connects to the imap server and runs Spamassassin on the messages and moves the Spam to another folder right away (btw, you can find the script at [http://www.rogerbinns.com/isbg/](http://www.rogerbinns.com/isbg/) - IMAP Spam Begone). But now I want to settle for a Evolution-based solution.

Anyone can help?

---

### Post by charlieg on 2005-08-09
I've found the Evolution + SpamAssassin combination to be quite effective.  I'm not sure if there's a Ubuntu how-to, but here's a the Gentoo equivalent which should mostly apply to Ubuntu:
[http://forums.gentoo.org/viewtopic-t-26006-highlight-spamassassin.html](http://forums.gentoo.org/viewtopic-t-26006-highlight-spamassassin.html)

Obviously step 1 will differ - use Synaptic to install spamassassin.

---

### Post by nocturn on 2005-08-09
Strange...  it is working for me on a Cyrus IMAP server...

---


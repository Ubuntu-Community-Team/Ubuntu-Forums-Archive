---
title: "IMAP clients failing since upgrade to hoary?"
date: 2005-05-08
forum: General Help
---

### Post by ubnik on 2005-05-08
Since roughly the time that I upgraded to hoary, a couple of users of thunderbird have had trouble getting mail from a DBMAIL 2.0.4 imap server.

The standard IMAP port, 143 is also accessible through an ssl tunnel using stunnel listening on 993.

Putting the client in SSL mode (almost?) always results in the client locking up or timing out when displaying the contents of a folder and producing log entries on the server like this:

```
May  8 14:13:13 hostname dbmail/imap4d[37283]: IMAPClientHandler(): error [Broken pipe] on write-stream
```

When the client is using uencrypted IMAP, it fails less often - folder contents and smaller messages can be viewed, but when attempting to view a larger messages e.g. > 10KB, it will lock up or time out, and produce log entries like this:

```
May  8 22:10:57 hostname dbmail/imap4d[568]: IMAPClientHandler(): error [Operation not permitted] on write-stream
```

I've tried using Evolution and the results are very similar.

I've also tried another i386 on a different network using a live cd (evolution only) and go the same results.

From both these networks I've tried connecting to these IMAP accounts using thunderbird 1.0.2 on OS X and it always works, so the problem appears to be isolated to Ubuntu Hoary.

My next thing to try will be a live CD of Warty to see if the problem appears in that.

This seems puzzling, as it sounds like some kind of TCP/IP thing - i.e. kernel related??? but I've not been able to find any fault with any other networking functions in hoary - e.g. http, ssh and smb transfers.

Has anyone else experienced anything like this?

Has anyone got any suggestions?

TIA

---

### Post by ubnik on 2005-05-09
Here's an update:  I've tried Evolution 2.0.2 on from the Warty Live CD and I don't see the problem.  I guess there's a good chance that the problem only shows up on dbmail servers. If this was happening with other IMAP servers I'd expect lots of other people seeing the same thing.

---

### Post by ubnik on 2005-05-19
I discovered the source of the problem.  I had PF (packet filter - firewall) rules running on the FreeBSD server. When I disabled PF, the problem disappeared.  The rules were somehow interfering with the tcp sessions - not just imap and imaps but also https and possibly anything else.  Strange thing is that it only affected ubuntu hoary (didn't try any other linux distro).  I've not tried to find out what specifically in the rules causes the problem, i've just gotten rid of PF for the time being :(.

---


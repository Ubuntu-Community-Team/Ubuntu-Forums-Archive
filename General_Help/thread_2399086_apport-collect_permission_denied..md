---
title: "apport-collect permission denied."
date: 2018-08-21
forum: General Help
---

### Post by arlenn2 on 2018-08-21
In reporting a bug, I have been requested to post log-files.  However, the apport-collect <bug>  command fails with "permission denied"

The authorization page:
 ([https://launchpad.net/+authorize-token?oauth_token=D03STSn4bd5sjSrgv***&allow_permission=DESKTOP_INTEGRATION](https://launchpad.net/+authorize-token?oauth_token=D03STSn4bd5sjSrgv***&allow_permission=DESKTOP_INTEGRATION))
should be opening in your browser. Use your browser to authorize
this program to access Launchpad on your behalf.
Waiting to hear from Launchpad about your decision...
Created new window in existing browser session.
ERROR: connecting to Launchpad failed: [Errno 13] Permission denied: '/home/abcefg/.cache/apport/launchpad.credentials'
You can reset the credentials by removing the file "/home/abcdefg/.cache/apport/launchpad.credentials"

I am prompted to log-in to the Launchpad, the launchpad login is successful.

I have found a previous bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073)

But it has been abandoned without resolution.

---

### Post by PaulW2U on 2018-08-21
> **arlenn2 said:**
> I have found a previous bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073)

But it has been abandoned without resolution.
I can't explain why the apport-collect function doesn't work but I am curious to know why you think that [bug 1788073]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073") has been abandoned. It's only been 12 hours since the last comment. If i could be bothered I could link to a bug that took seven **years** to be fixed. Admittedly it wasn't a bug in an important application but it really did take that long to be fixed.

The bug reporting process has been followed correctly but you now have to wait for alternative instructions from the Ubuntu Kernel team who have over 6000 bug reports to deal with of which over 800 have been marked as being of "High importance". It will take time before anyone looks at or responds to that bug report.

---

### Post by deadflowr on 2018-08-21
>  am curious to know why you think that bug [lpbug]1788073[/lpbug] has been abandoned.
I thought so too, but perhaps the post is suppose to refer to this bug: [lpbug]1779817[/lpbug]
which is also not really abandoned either.

---

### Post by PaulW2U on 2018-08-21
> **deadflowr said:**
> I thought so too, but perhaps the post is suppose to refer to this bug: [lpbug]1779817[/lpbug]
which is also not really abandoned either.
Anyone reading bug reports really needs to right mouse click on usernames to see who is actually responding and might actually be in a position to fix a particular bug.

If a **developer** responds to a bug report then I think that the bug has to an extent been prioritised. Time is limited. Developers, especially paid Canonical employees,  will apportion their time between fixing bugs and moving Ubuntu forward towards the next release and whatever it has been decided to include.

A bug that is seen to affect just **one** person might never be fixed. :(

---

### Post by Yellow Pasque on 2018-08-21
> You can reset the credentials by removing the file "/home/abcdefg/.cache/apport/launchpad.credentials"

^Have you tried to do that?

---

### Post by arlenn2 on 2018-08-22
> **arlenn2 said:**
> In reporting a bug, I have been requested to post log-files.  However, the apport-collect <bug>  command fails with "permission denied"

The authorization page:
 ([https://launchpad.net/+authorize-token?oauth_token=D03STSn4bd5sjSrgv***&allow_permission=DESKTOP_INTEGRATION](https://launchpad.net/+authorize-token?oauth_token=D03STSn4bd5sjSrgv***&allow_permission=DESKTOP_INTEGRATION))
should be opening in your browser. Use your browser to authorize
this program to access Launchpad on your behalf.
Waiting to hear from Launchpad about your decision...
Created new window in existing browser session.
ERROR: connecting to Launchpad failed: [Errno 13] Permission denied: '/home/abcefg/.cache/apport/launchpad.credentials'
You can reset the credentials by removing the file "/home/abcdefg/.cache/apport/launchpad.credentials"

I am prompted to log-in to the Launchpad, the launchpad login is successful.

I have found a previous bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1788073)

But it has been abandoned without resolution.


Copy/Paste error the abandoned bug, is this one.
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1656504](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/1656504)

Which is an identical to issue I am seeing when trying provide information for my bug report '073

---

### Post by arlenn2 on 2018-08-22
> You can reset the credentials by removing the file "/home/abcdefg/.cache/apport/launchpad.credentials" 			 		 	 
[quote]^Have you tried to do that?[/quote]


Yes, launchpad.credentials does not exist.

---

### Post by arlenn2 on 2018-08-22
> **deadflowr said:**
> I thought so too, but perhaps the post is suppose to refer to this bug: [lpbug]1779817[/lpbug]
which is also not really abandoned either.

I had a copy/paste error, the correct link is below.

---


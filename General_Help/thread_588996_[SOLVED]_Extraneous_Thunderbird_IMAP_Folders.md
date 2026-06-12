---
title: "[SOLVED] Extraneous Thunderbird IMAP Folders"
date: 2007-10-23
forum: General Help
---

### Post by wsmoser2004 on 2007-10-23
I have a semi-annoying problem with Thunderbird where it shows me a whole bunch of folders for my IMAP E-mail account that I don't actually want to subscribe to.  The only ones I really want are INBOX, INBOX.Sent, INBOX.Trash, and INBOX.Drafts.  However, Thunderbird for some reasons has other ones there like "/var", "mail", "/users", and extraneous "Sent" and "Trash" folders.  I have Thunderbird configured so it uses all the INBOX.* folders, but for some reason all of these other folders keep showing up.

Occasionally I am able to delete them from within Thunderbird, but they always come back when I restart Thunderbird.  I am also afraid to delete some of them (for example, one of them is my username on the system I'm getting my mail from...I don't want it to delete my home directory on that system!)  Maybe it is a configuration problem on the server side, I don't know.

I've also tried to unsubscribe from those folders in Thunderbird, but for most of them there is no checkbox next to the folder to (un)subscribe!  I'd really like to get rid of all these unused folders, since it would be nice for that column on the left to only be about four items high as opposed to 10...

As far as I know the only folders that exist on the server are the ones that start with INBOX...and I'm sure I don't have a folder called /var or /users in my E-mail...

---

### Post by wsmoser2004 on 2007-10-24
I figured out the problem!  It was a server problem.  I logged into the system I get my mail from, and in my home directory was a ".mailboxlist" file.  In there were all of those extra mailboxes, so I just commented all of the unneeded ones out.  Now it works great!

---


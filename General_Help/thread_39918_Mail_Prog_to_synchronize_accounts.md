---
title: "Mail Prog to synchronize accounts"
date: 2005-06-07
forum: General Help
---

### Post by hal8000 on 2005-06-07
I have a laptop and a desktop computer both running Ubuntu 5.04.  At the moment
I'm pulling my email via Wanadoo's webmail page: 
[http://email02.wanadoo.co.uk/webmail/login.html?null](http://email02.wanadoo.co.uk/webmail/login.html?null)

This is good because I can keep email in sync between the two machine.

Is there any linux mail program or utility that I can use to download email and keep
changes in sync between machines?
I've tried Evolution with the option (do not remove email from server) which works
but when I delete a message it is not deleted at the mail server.

Any help or recommendations appreciated; thx in advance.

---

### Post by Alexander Kirillov on 2005-06-07
[QUOTE=hal8000]I have a laptop and a desktop computer both running Ubuntu 5.04.  At the moment
I'm pulling my email via Wanadoo's webmail page: 
[http://email02.wanadoo.co.uk/webmail/login.html?null](http://email02.wanadoo.co.uk/webmail/login.html?null)

This is good because I can keep email in sync between the two machine.

Is there any linux mail program or utility that I can use to download email and keep
changes in sync between machines?
I've tried Evolution with the option (do not remove email from server) which works
but when I delete a message it is not deleted at the mail server.

Any help or recommendations appreciated; thx in advance.[/QUOTE]
 The only way I know of achieving this is by using  IMAP: if you are getting the mail using the IMAP protocol, you can delete or move emails on the server from your email program (e.g. Evolution). POP does not allow this, and no email client can possibly change that: the only options for POP is downloading all new emails erasing tehm formt eh server, or downloading them all leaving a copy on the server. No other options - it is not a limitation of a email client but of POP protocol. 

Unfortunately, I do not know if Wanadoo offers IMAP...

---

### Post by gilf on 2008-02-24
Yes but what about periodically synchronizing the laptop and desktop downloaded mail folders via network or USB connection between them?

It's been awhile since I used it, but I believe Lotus Notes allowed synchronizing in this way.

Anything similar available in Ubuntu?

Ideally it would be a small app -- not like full-fledged Lotus Notes, which is practically an OS itself.


(ps I don't think POP restricts things quite so much as indicated above. How things are handled depends on the client. For instance, a windows app, Mailwasher, can work with the server on an individual item basis without downloading. Early versions of Mailwasher used to be free, and it runs well in Wine -- I use it for screening and deleting spam before actually downloading. Still, it is not a means of synchronizing mail folders on different computers, and that's what we're asking about here).

Thanks!

---

### Post by gilf on 2008-02-25
Well I've now researched and tried tests with rsync and Unison. Both have the potential to sync the folders, and if all you want is to sync a laptop after a business trip with a desktop, no problem.

But you can only sync the mail file, not the mail itself. So if you can't do mail on both computers before syncing. It has to be one or the other alone. If email was kept as individual files instead of a big database files, syncing would be easy.

However, I do have a lead on someone who has written some code to automatically merge email files that have a diff (the case of the two computers working on mail between syncs) if that works out, I'll combine the two stages of syncing and merging diffs, and write a How-to for this as a separate thread.

Any other assistance or suggestions for an easier way at this stage are still welcome, of course.:)

---

### Post by Mr. C. on 2008-02-25
How mail is stored locally is up to the client.  It is not safe to just run rsync, and assume copying files back and forth is sufficient.

Some clients will maintain mail in mbox files, others can use Maildirs, still other's can use complex databases (eg. Outlook).  And still others are server-based (Exchange, Lotus Notes), and have built in replication, offline use, etc.  And each may or may not have metadata about the mail database.

If you are going to attempt to sync email databases between two clients, you will have to learn what the rules are for a given client.  You may have to first quit the clients, then copy a given set of files, delete others, etc.

POP will allow the client to specify *not* to delete the message upon retrieval.  Each client can issue a permanent delete command.  I do not believe Evolution is unable to permanently delete a POP message. Rather, it is likely there is a setting in your Wanadoo account to allow permanent deletion.

However, this begs the question - what protocols does Wanadoo support for accessing mail remotely?

MrC

---

### Post by gilf on 2008-02-25
Yup, as I already said, rsync and Unison won't do what is needed..

Personally, I'm just interested in syncing Thunderbird. Not in trying to come up with a solution for every mail client in the world. Though what works forThunderbird will probably work for Evolution, so that would have application to a lot of people..

Thunderbird uses a flat database text mail file. I succeeded in merging two asynchronous copies this evening using a modification of a program and script I found on a web search which was geared to Evolution. If it works out after more trials, I'll put it up on the forum for others to comment on or test.

Mr. C, I think the OP who was interested in Wanadoo may be long gone -- note the date of the first post! I missed that when I responded to the thread.

Still, it's an interesting topic. And maybe we can make some progress on it.

---

### Post by danf_1979 on 2008-04-23
Any update on this? I was trying to use unison to synchronize evolution between my laptop and desktop, but it failed. :/

If you got any solution please post :P

---

### Post by hal8000 on 2008-05-02
My original post was in 2005. Someone replied 3 years later. However, I now
have an even simpler solution - webmail.
Yahoo, Gmail, Hotmail and most ISP's these days allow you to log into a mail account from your web browser. Its fast, and as your mail is stored on the remote mail server all changes are made remotely. Therefore there is no need to waste time synchronising as you will always see current changes, from any machine, from any location... good bye forever Outlook

---


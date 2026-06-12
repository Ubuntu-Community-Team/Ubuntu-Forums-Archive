---
title: "Synchronising email between multiple computers"
date: 2007-12-25
forum: General Help
---

### Post by elicoten on 2007-12-25
Hi

I have a few email accounts, unfortunately including a Hotmail account which is a real pain to deal with. Anyway the problem is that I use more than one computer so I need to somehow be able to get my email son whichever computer I choose to.

Previously I had all my email accounts setup on one (Windows) machine. I used Thunderbird for most of the accounts, and Windows Live Mail for the hotmail account.

I now have a Ubuntu machine and I need to be able to send and receive emails from it and still keep it synchronised with the Windows machine. The hotmail account is actually the least of the problem because whatever I do on Webmail will get syncronised with Windows Live Mail and therefore that isn't a problem. The remaining accounts are setup in Thunderbird. Unfortunately only one of them supports IMAP.

I have a few ideas but I want to know what else is possible, or which of these ideas is the best.

1) Use Thunderbird on the Ubuntu Machine and get it to use the same mail folders as are on the windows (by mounting a windows share into the file system and store the mail on that). If I setup thesame settings on both machines hopefully the macine would simply continue to download as if the other didn't exist.
2) Similar to 1) except put the whole profile on a samba share and get Thunderbird to run from the shared profile
3) Similar to 2) except use Wine + the Windows Thunderbird on the Ubuntu machine in case the Linux Thunderbird cannot open a Windows profile
4) Try evolution and see if that can do something (synchronisation-wise) that Thunderbird can't.
5) Use Remote Desktop to access my main machine and just work from that all the time. At the moment that's not possible because I'm having a problem with Remote Desktop (see [http://ubuntuforums.org/showthread.php?t=648421](http://ubuntuforums.org/showthread.php?t=648421)
6) Just set up each computer to leave the messages on the POP server and have each computer download the messages locally. Keep the sent items folder on a shared location so that sent messages are all kept in one place.

Are there any other ways of achieving this? Thanks in advance

---

### Post by TidusBlade on 2007-12-25
I wouldn't really suggest remote desktop, might wanna try Evolution before anything else aswell, I would try the first one...

---

### Post by elicoten on 2007-12-25
What can Evolution do that Thunderbird can't (bear in mind that Evolution cannot be installed on Windows and Thunderbird can?)

I did try the first one but Ubuntu wanted to redownload every single message that had ever been on the POP3 server and in the end I had to use the Remove Duplicate Messages extension to clean up the mess!

Why wouldn't you suggest remote desktop?

---

### Post by elicoten on 2007-12-27
bump

---

### Post by psusi on 2007-12-27
If you have a machine that is always on/online, you can set it up as a server.  Have it download all the messages to itself using fetchmail, and serve it back out via IMAP.  I have a server set up like that using dovecot for the IMAP server and postfix for SMTP.  I configured fetchmail to run every 15 minutes and download all my mail via POP3 and drop it into a local Maildir on the server, which dovecot serves via IMAP.

---

### Post by elicoten on 2007-12-28
If I was going to do this, I would do it on the Windows Machine. What software is there available for Windows that can do this?

Thanks very much for your advice

---

### Post by psusi on 2007-12-28
None that I know of.

---

### Post by elicoten on 2007-12-29
Any other advice/ideas?

Thanks for all your help & advice so far

---

### Post by Crakie on 2007-12-29
I used to share email between XP and Ubuntu with Thunderbird, but on the same machine. It was really easy to set up, basically putting the mail on a fat32 partition and showing both the Windows and Ubuntu client where to look for it. Nowadays I guess a NTFS-partition would do as well, since NTFS read/write support in Linux is considered stable. You could do the same, but you need to put it in a folder that is shared across the network. Samba seems perfect for that job. 

P.S. I am assuming your two machines are in a network, of course.

---

### Post by elicoten on 2007-12-29
The machines are on a network but I found that when I did that, the Ubuntu machine kept trying to redownload every single message that was ever received? Also what about if both computers have Thunderbird open at the same time? Does it matter if the computer that's hosting the share also has Thunderbird installed?

---

### Post by HermanAB on 2007-12-29
There are many kludges, but in the end the only real solution is to run your own mail server and use IMAP or Webmail from all the clients.  Here is a mail server that is exceptionally easy to install and zero maintenance, with all the features you need and then some: [http://citadel.org](http://citadel.org)

Using Easy install, it takes about 20 minutes to set up.  All you need is a 'server' account from your ISP and a spare PC.

Cheers,

Herman

---

### Post by jeffus_il on 2007-12-29
I use Thunderbird to access imap on GMail, and all other accounts forward to the imap server. Gmail will also fetch pop mail from other accounts, so this could solve your problem without making any changes.

---

### Post by elicoten on 2007-12-29
I must say I like the idea of using the GMail POP access - its is one I never thought of, and the whole reason I posted on this forum... That way I could also use the GMail Spam filter. I might well try that. I have a couple of questions:

1) When downloading Email through GMail's IMAP server, can Thunderbird be configured to download all messages locally for offline viewing?
2) How does GMail distinguish between messages fetched from other POP3 servers, and message received to the GMail account?

Thanks a million this could be the solution.

---

### Post by jeffus_il on 2007-12-29
Thunderbird can be configured at a folder level for dowloading for offline viewing.

Am looking into your no. 2 question.

---

### Post by jeffus_il on 2007-12-29
I look at the address sent to in the message header to see which account the mail was originally sent to.

---

### Post by jeffus_il on 2007-12-29
Ah! fFound this in the GMail help:
"Label incoming messages.
If you'd like to automatically label all messages that are retrieved from your non-Google account, select this option. You can choose to use the predefined label (your email address), or you can select an existing label or create a new one from the drop-down list."

---


---
title: "Dovecot configuration problem?"
date: 2014-09-28
forum: General Help
---

### Post by JKyleOKC on 2014-09-28
[COLOR="#FF0000"]EDIT: See post #3 for latest developments in this continuing problem...[/COLOR]

I'm in the process of replacing a quite reliable Xubuntu 12.04.5 installation with Xubuntu 14.04.1, and transferring as much as possible of the configuration files over to retain the exact same functionality. The two systems are on separate drives in the same box, making it possible to directly compare configuration files and also to copy data files across quickly.

Most of the changeover has gone well, but moving my mail servers (needed to originate reports across my LAN) is turning out to be a headache. I think I've finally gotten Postfix configured correctly again, but Dovecot is giving me serious resistance. Here's the pertinent excerpt (with addresses sanitized) from /var/log/mail.log after issuing a "sudo postfis flush" command to try to jar loose six test messages that have been stuck in the deferral queue for some 17 hours now:```
Sep 27 23:57:37 mehitabel postfix/qmgr[13965]: 9F809C24F3: from=<root@jimkyle.xxx>, size=19507, nrcpt=1 (queue active)
Sep 27 23:57:37 mehitabel **dovecot: lda(root): Error: chdir(/root/) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root, dir owned by 0:0 mode=0700)**
Sep 27 23:57:37 mehitabel dovecot: lda(root): Error: chdir(/root) failed: Permission denied
Sep 27 23:57:37 mehitabel **dovecot: lda(root): Error: user root: Initialization failed: Initializing mail storage from mail_location setting failed: stat(/root/Maildir) failed: Permission denied (euid=65534(nobody) egid=65534(nogroup) missing +x perm: /root, dir owned by 0:0 mode=0700)**
Sep 27 23:57:37 mehitabel dovecot: lda(root): Fatal: Invalid user settings. Refer to server log for more information.
Sep 27 23:57:37 mehitabel postfix/local[14444]: 9F809C24F3: to=<root@jimkyle.xxx>, orig_to=<root>, relay=local, delay=58955, delays=58954/0.01/0/0.06, dsn=4.3.0, status=deferred (temporary failure)

```The two lines I've emphasized make it quite clear what is going wrong, but I've not been able to find any place to force the proper user when dovecot tries to put something in root's Maildir!

And I've not been able to locate that "server log" to "get more information."

All was working well in the old system, but apparently either Postfix or Dovecot, or maybe both, have undergone critical change in the past couple of years. Will someone steer me through this minefield so that I can get my logwatch reports and cron reports once again?

---

### Post by JKyleOKC on 2014-09-28
Well, I'm making some slight progress, but the main problem remains unsolved.

I've found that Dovecot is delivering incoming messages to my ~/Maildir/new directory, but not in final format. A typical filename is > "1411939266.M371346P21511.mehitabel,S=925,W=947" (which was a test message sent from another account this afternoon). Double-clicking on any of these files opens Thunderbird for writing a new message that includes the file itself as an attachment. Viewing the attachment with mousepad reveals the full source of the incoming message.

Based on that discovery, I began experimenting with the ImportExportTools add-on to Thunderbird, and found that I could use its "import message" capability to bring the message into TBird's mailbox structure. I had to create a folder "00Imports" in TBird (to keep the experiments from affecting my production folders), then select that folder, launch the add-on, select "import message," change the file-type option in the resulting file picker dialot to "all files," and could then select any or all files in the ~/Maildir/new folder for transport. 

They then appeared in the "00Imports" folder and could be moved to appropriate final destinations just as if TBird had done its intended job automagically, as it had done for years.

This procedure offers a possible workaround, but is obviously impractical for extended use. Google searches reveal almost no discussion of configuring postfix, dovecot, and tbird for pop3 use -- the few hits I received describe imap setup rather than pop3. Thunderbird's help facilities make no mention at all of anything resembling FireFox's "about:config" detailed configuration edit capability, nor do they even acknowledge the existence of Maildir and mbox operations.

All suggestions are welcome. I'm beginning to consider abandoning 14.04 and staying with 12.04 for the next seven months! Or maybe even jumping ship to full Debian, but I do like the atmosphere here better...

---

### Post by JKyleOKC on 2014-09-30
Still more progress, but the problem now appears to be in Thunderbird itself rather than in Dovecot.

After making (and unmaking) several changes to the Dovecot and Postfix configuration files, I did change the Thunderbird setting for the local server to use the new (and still experimental) "maildirstore" instead of the original "berkeleystore" setting for its "storeContractID" and tested again. This time, the incoming message went from ~/Maildir/new to ~/Maildir/cur and I got a fleeting message that something had been expunged, but the "local" account in TBird had no inbox listed. After shutting down TBird I opened up its "prefs.js" file and changed the storeContractID setting back to the original -- and when I re-opened TBird, the test message was automagically retrieved. However this seems to have been a one-time action, not a final fix.

It appears that the best solution at this point might be to install the Dovecot imap modules and convert that account from pop3 to imap. The new module in TBird appears to be for imap only, while the older module apprears to no longer be proessing pop3 traffic from Maildir boxes!

---

### Post by JKyleOKC on 2014-10-01
> **JKyleOKC said:**
> However this seems to have been a one-time action, not a final fix.As of this morning, it appears to have been a final fix! Everything came through just as it did with the old system, even though I had made no more configuration changes, so I'm marking the thread as solved.

---


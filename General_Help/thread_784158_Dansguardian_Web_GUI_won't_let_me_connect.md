---
title: "Dansguardian Web GUI won't let me connect"
date: 2008-05-06
forum: General Help
---

### Post by alishad on 2008-05-06
I was able to log into the web gui using the backuppc user and password.  For the past couple of days, it won't let me connect via web interface.  I can still connect to it through ssh but I need the GUI back up and working. Any suggestions on what I should check/change?

---

### Post by alishad on 2008-05-06
I was using the web interface to manage Backuppc  For the past week, it won't let me log into the web interface using the backuppc user.  I can still SSH to the server but I need to get the web interface back up.  Any ideas/suggestions on what to check.

---

### Post by Scunge on 2009-05-14
I am having the same/similar problems accessing BackupPC.

I first found this problem recently with my backup machine using Dapper and BackupPC version 2.1.2. I made do for a while, using Lynx over SSH to access it (it's slow and has no GUI), but since an upgrade to Hardy was due anyway, I installed a fresh Hardy command-line system on a clean disk and hence version 3.0.0 of BackupPC out of the repositories.

No change.

I can SSH from other machines onto the backup machine (although those sessions freeze occasionally, may be related?) and the backup machine can reach other machines fine. So the network setup seems ok in general. However, I can't get the web interface to come up on anything except the backup machine itself; trying on other machines asks for the user and password, then just "Waiting for <machine>..." forever.

The fact that I can access BackupPC on the backup machine shows that apache is performing ok, perhaps it's some setting to do with external access. During installation, I chose 'apache2' since that was what was in the apt-get package list to download. Also, it used to work fine, it just stopped one day. So it seems some update broke something.

Why should external access parameters be changed by an update, or simply be wrong during a clean installation? I have made no changes to apache from what is done by default during installation. Doesn't make sense, so I wonder if the problem is not apache's settings after all. But I have no idea where to start to look.

And a side question: In BackupPC 2.1.2, using Lynx on the backup machine worked okay, but in 3.0.0 the links for performing backups and restores are just shown as "[BUTTON]" and I can't reach them. Viewing the source shows they're form buttons. Can someone tell me either a) how to allow access to these buttons in Lynx, or b) what a direct URL would be to get BackupPC to perform full and incremental backups for a given machine?

Thanks in advance for any help.

Edit: It seems the backup machine can't, in fact, do any backups successfully. It keeps giving "Connection reset by peer" in the Xfer Log. Perhaps the SSH problem I mentioned above is indeed related?

Edit 2: Just noticed the following in the Xfer Log, might or might not make a difference:
```
Running: /usr/bin/ssh ...
Got remote protocol 29
Negotiated protocol version 28
```Both SSH files are the same size and date on both machines.

Edit 3: Just installed BackupPC on an existing Hardy desktop machine and it seems to all work fine, no connection resets or anything. I'd have guessed it's a hardware issue with the other machine or something, except that it did the post-installation updates from the repositories, and the installation of BackupPC and associated packages fine.

---


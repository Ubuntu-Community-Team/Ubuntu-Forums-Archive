---
title: "can no longer open files over network (NAS)"
date: 2012-12-16
forum: General Help
---

### Post by raydar on 2012-12-16
I have a USB hard drive connected to my router and shared via Samba. I originally had no problems navigating to or opening files on that shared drive from my two Ubuntu 12.10 machines, but that suddenly changed for no reason I can identify; now I can navigate to them, but not open them.

When I try to open a video, the application starts and then hangs and has to be killed (no matter whether VLC, Totem, SMPlayer, etc., except gxine will play them on one of the machines but no the other machine). 

When I try to open a document, LibreOffice Writer similarly starts, perpetually displaying the splash graphic, but never opens the document.

But I can copy files to and from the shared drive with no problems, and that's how I've been playing videos and working with documents for a couple of weeks while trying to figure out how to fix the problem. I've disconnected and reconnected the drive and removed the and recreated the share in my router's web interface, but that didn't help. The only thing I've noticed is that I can't access the shared drive if I open Nautilus as root with sudo.

Anyone have any suggestions what's going on?

---

### Post by raydar on 2013-01-07
I still haven't succeeded in figuring out a solution. Anyone have any ideas?

---

### Post by tgalati4 on 2013-01-07
Check the log files in /var/log/samba.  See if there is anything obvious around the time it stopped working.  Post anything that you don't understand.

Open a terminal:

```
cd /var/log/samba
ls -la
less log.smbd

```

Spacebar to page forward, "q" to quit.  Check all of the files in the samba directory for errors.

---

### Post by luvshines on 2013-01-08
How has the share been defined in smb.conf ?

If you are experiencing access issues, external HDD generally require 'force user = <valid-system-user-with-access>' parameter to be used

---

### Post by bkaplan on 2013-01-08
I am experiencing exactly the same issues and behavior reported above by raydar when I try to edit files that are in my samba network shares (on my network file server running ubuntu 12.04 server edition, with terabyte raided drives).  These shares are longstanding and have been trouble-free on my network, and they have not changed recently.

Although I can copy and move files, unopened, through the network via the samba share, I have the same issues described above in trying to open files in these samba shares with libreoffice--I'm getting a frozen splash screen and a hung application that has to be killed from the terminal.  This happens with both libreoffice writer and spreadsheet documents.  Once I get such a hang, I can no longer unmount the share.  I did not observe this behavior happening until the last couple of days--previously, I was able to edit these same files in these same samba shares with no issues.

Interestingly, I can open and edit these same network files--with no problems--over an sftp: connection.  Thus, I have convinced myself that it is not a problem with my Libreoffice installation and, rather, has something to do with samba.

Did something change in a recent samba update?  Is there a known fix?

Thanks.

Barry

---

### Post by mcmook on 2013-03-28
Bump.  Same issue for me.  No fix yet?

---

### Post by SeijiSensei on 2013-03-28
If you have the option of using NFS either in place of, or alongside, Samba, I'd definitely recommend that.  I have both Samba and nfs-kernel-server running on my central file server.  For sharing to *nix machines, NFS is definitely a better choice than Samba.  That's especially true with streaming videos like the OP was talking about.

---


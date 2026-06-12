---
title: "Using ftp or rsync"
date: 2020-04-16
forum: General Help
---

### Post by silentjay2 on 2020-04-16
Hi,

Ive searched and could not find an example of what im looking to do. I need a clean way to transfer files from a remote server to a local pc twice a day. As part of this, i need to be able to remove files from the remote server without affecting whats local and also i need to be able to auto skip existing files or resume files. I used to do this as part of scheduling inside an ftp app for windows. Now, i have ubuntu server on both sides. If ftp inside a cron job is the answer, can someone show me how to compile that?

thanks,

Jason

---

### Post by aljames2 on 2020-04-16
FTP is not secure so no to that.  SFTP is preferred to plain old ftp.  Rsync is for syncing source & destination.  While it is true Rsync can be used as a utility to copy files, or to assist in backup schemes, it can be dangerous if the correct options are not used.

The part that concerns me about your plan is you want to wipe the source location after the files have been copied over.  If you’re not careful with Rsync, your destination could also be wiped as it attempts to sync by default.  However some of the options in Rsync do allow you to preserve destination and only add to it.  You should stay away from -a and —delete options.  Others on this forum may be able to offer an example of a safe Rsync command for this.  Also, see the Rsync manpage.  

It sounds like you may need a custom script to do what you want.

I hope you have extra backups in addition to the destination you are pulling to.

---

### Post by silentjay2 on 2020-04-16
id prefer to use sftp or ftps, they are both options, in fact i mispoke and would be connecting over ftps. i  mentioned rsync because it was mentioned elsewhere. the local is the backup. I just want the files to come down and not fail because the same files are there already. I need a switch in the sftp or ftps command that either skips existing files or resumes.

---

### Post by HermanAB on 2020-04-17
Hmm, I would use rsync one SSH and I won't delete.  Deleting files is always dangerous and probably should not be automated, because there are so many unexpected ways in which it can go wrong.

Maybe you should also look at a Distributed File System.

For an efficient backup strategy, have a look at this:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---


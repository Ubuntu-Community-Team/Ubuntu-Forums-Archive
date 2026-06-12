---
title: "SSH in Gnome"
date: 2007-10-16
forum: General Help
---

### Post by Tobbera on 2007-10-16
When I use nautilus-connect-server to connect to a SSH server I get strange file-permission information when checking properties on files in the mounted ssh-folder. It says "unknown" as owner no matter which file/folder I check.  The information shows up fine if browsing the same directory through NFS. The information also shows up fine if browsing the same directory with command line ssh. 

Sorry about the Swedish language in the system but I think you recognize the dialog boxes.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46500&stc=1&d=1192543569[/IMG]


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46501&stc=1&d=1192543697[/IMG]

---

### Post by p_quarles on 2007-10-16
SSH remote login doesn't allow you to transfer files between computers. Since Nautilus is running on the local machine, it doesn't have full access to the files on the remote machine.

SSH includes, however, two ways of transferring files between machines. One is scp (secure copy), which probably isn't what you're looking for. The other is sftp, which probably is. Nautilus might support sftp (try choosing that instead of ssh). If not, you can get Filezilla, which definitely does support sftp. That will allow you full access (with password) to the files on the remote machine, via the GUI on the local machine.

---

